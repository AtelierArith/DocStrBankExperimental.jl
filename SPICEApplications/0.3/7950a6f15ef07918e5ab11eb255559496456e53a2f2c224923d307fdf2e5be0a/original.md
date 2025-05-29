```julia
frmdiff(
;
    kernels,
    from1,
    to1,
    frame1,
    supporting_kernels1,
    from2,
    to2,
    frame2,
    supporting_kernels2,
    angular,
    angularframe,
    start,
    stop,
    numpoints,
    timestep,
    timeformat,
    report,
    rotation,
    units,
    sigdigs,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

FRMDIFF is a program that samples orientation of a reference frame known to SPICE or computes differences between orientations of two reference frames known to SPICE, and either displays this orientation or these differences, or shows statistics about it or them.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument              | Equivalent                                                                | Description                                     |
|:--------------------- |:------------------------------------------------------------------------- |:----------------------------------------------- |
| `kernels`             | `-k  <supporting kernel(s) name(s)>`                                      | supporting kernel(s) name(s)>                   |
| `from1`               | `-f1 <first``from'' frame, name or ID>`                                   | first "from" frame, name or ID                  |
| `to1`                 | `-t1 <first``to'' frame, name or ID>`                                     | first "to" frame, name or ID                    |
| `frame1`              | `-c1 <first frame for coverage look up, name or ID>`                      | first frame for coverage look up, name or ID    |
| `supporting_kernels1` | `-k1 <additional supporting kernel(s) for first file>`                    | additional supporting kernel(s) for first file  |
| `from2`               | `-f2 <second``from'' frame, name or ID>`                                  | second "from" frame, name or ID                 |
| `to2`                 | `-t2 <second``to'' frame, name or ID>`                                    | second "to" frame, name or ID                   |
| `frame2`              | `-c2 <second frame for coverage look up, name or ID>`                     | second frame for coverage look up, name or ID   |
| `supporting_kernels2` | `-k2 <additional supporting kernel(s) for second file>`                   | additional supporting kernel(s) for second file |
| `angular`             | `-a  <compare angular velocities: yes│no (default: no)>`                  | compare angular velocities                      |
| `angularframe`        | `-m  <frame for angular velocities: from│to (default: from)>`             | frame for angular velocities                    |
| `start`               | `-b  <interval start time>`                                               | interval start time                             |
| `stop`                | `-e  <interval stop time>`                                                | interval stop time                              |
| `numpoints`           | `-n  <number of points: 1 to 1000000 (default: 1000)>`                    | number of points                                |
| `timestep`            | `-s  <time step in seconds>`                                              | time step in seconds                            |
| `timeformat`          | `-f  <time format: et│sclk│sclkd│ticks│picture_for_TIMOUT (default: et)>` | time format                                     |
| `report`              | `-t  <report: basic│stats│dumpaa│dumpm│dumpqs│dumpqo│dumpea│dumpc│dumpg>` | report                                          |
| `rotation`            | `-o  <rotation axes order (default: z y x)>`                              | rotation axes order                             |
| `units`               | `-x  <units for output angles> (only for -t dumpaa and -t dumpea)`        | units for output angles                         |
| `sigdigs`             | `-d  <number of significant digits: 6 to 17 (default: 14)>`               | number of significant digits                    |
