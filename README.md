# Netgear PoE Multi Controller

## One panel for PoE across every Netgear switch in the design.

Rebooting a room full of PoE devices should not mean visiting each switch plugin to turn ports off and on again.

Each Netgear switch plugin controls a single switch. With several of them in a design, power cycling cameras, access points or displays across the building, while leaving uplinks and critical devices alone, takes a lot of clicking and a lot of wiring.

**The Netgear PoE Multi Controller is a Q-SYS plugin that sits on top of your existing Netgear switch plugins.** Pick which switches it controls, then switch their PoE one by one, in groups, or all at once from a single panel, with combined status in one place.

### What you get
- **Select and switch.** Select any switches and press PoE On or PoE Off. Every row also has its own On, Off and power toggle.
- **Press and hold for All On / All Off.** A deliberate hold, so nobody drops power to the whole site by accident. A text box decides which switches are included, such as `1-4` or `all except 3`.
- **Port exceptions.** Choose which ports get switched, globally or per switch, such as `all except 1-2`.
- **Combined status.** One status for every switch, with the problem switches listed, plus ports on and ports powered.
- **Optional metering.** PoE draw per switch and in total.

# In detail

## Setup

Set **Switch Count** (default 4) in the plugin properties. On the Setup page, pick a Netgear plugin for each row from the dropdown. Only Netgear switch plugins are listed. Give each row a display name if you like.

Each Netgear plugin needs:

- **Script Access** set to Script or All.
- **Write Access** set to Yes. Without it, the switch plugin does not expose its PoE or port controls, and this plugin will say so in that row's status.

## PoE or Port

The **Control** property chooses what the plugin switches. **PoE** turns port power on and off. **Port** enables and disables the ports themselves. In Port mode, the switch's core and trunk ports are never disabled.

## Choosing ports

Port lists accept plain text:

- `all` or `none`
- `1-6` or `1-4, 6-8`
- `all except 1` or `!5, !7`

Set a default for On and a default for Off, then override either per switch. Leave a per-switch box blank to use the default. The Setup page shows the resolved list for each switch so you can check it before using it.

Because On and Off lists are separate, a switch can be switched "off" while one port stays powered. The switch's LED and state read Off once everything in its Off list is off.

## All On / All Off

Press and hold either button for the hold time (default 2 seconds). A progress bar fills while you hold, and letting go early cancels. Switches are changed in turn with a short stagger so the load comes back gradually.

## Status

Each row mirrors the status of its Netgear plugin. The combined status is OK when all are OK, Compromised when some are not, and Fault when none are. In emulation it reports OK so designs can be tested without hardware.

## Metering

Metering is off by default. Turn it on in the plugin properties to add PoE draw per switch and in total.

## Other settings

- **Deselect After On/Off.** Off by default, so your selection stays put after switching.
- **Hold Time, Stagger and Poll Interval.** Adjustable on the Setup page.
- **Debug Print.** A property that writes what the plugin is doing to the Q-SYS log.

The plugin only controls Netgear plugins already in the design. It does not talk to the switches directly.
