```julia
spkdiff(
;
    kernels,
    body1,
    center1,
    frame1,
    supporting_kernels1,
    body2,
    center2,
    frame2,
    supporting_kernels2,
    start,
    stop,
    timestep,
    numstates,
    timeformat,
    sigdigs,
    report,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

SPKDIFF provides means for comparing the trajectories of two bodies or sampling the trajectory of a single body using data from SPICE kernels.

# Extended Help

!!! warning
    All descriptions below were manually parsed from the commandline program's help/usage output.


| Argument              | Equivalent                                                                  | Description                                                               |
|:--------------------- |:--------------------------------------------------------------------------- |:------------------------------------------------------------------------- |
| `kernels`             | `-k  <supporting kernel(s) name(s)>`                                        | -k  <supporting kernel(s) name(s)>                                        |
| `body1`               | `-b1 <first body name or ID>`                                               | -b1 <first body name or ID>                                               |
| `center1`             | `-c1 <first center name or ID>`                                             | -c1 <first center name or ID>                                             |
| `frame1`              | `-r1 <first reference frame name>`                                          | -r1 <first reference frame name>                                          |
| `supporting_kernels1` | `-k1 <additional supporting kernel(s) for first SPK>`                       | -k1 <additional supporting kernel(s) for first SPK>                       |
| `body2`               | `-b2 <second body name or ID>`                                              | -b2 <second body name or ID>                                              |
| `center2`             | `-c2 <second center name or ID>`                                            | -c2 <second center name or ID>                                            |
| `frame2`              | `-r2 <second reference frame name>`                                         | -r2 <second reference frame name>                                         |
| `supporting_kernels2` | `-k2 <additional supporting kernel(s) for second SPK>`                      | -k2 <additional supporting kernel(s) for second SPK>                      |
| `start`               | `-b  <interval start time>`                                                 | -b  <interval start time>                                                 |
| `stop`                | `-e  <interval stop time>`                                                  | -e  <interval stop time>                                                  |
| `timestep`            | `-s  <time step in seconds>`                                                | -s  <time step in seconds>                                                |
| `numstates`           | `-n  <number of states: 2 to 1000000 (default: 1000)>`                      | -n  <number of states: 2 to 1000000 (default: 1000)>                      |
| `timeformat`          | `-f  <output time format (default: TDB seconds past J2000)>`                | -f  <output time format (default: TDB seconds past J2000)>                |
| `sigdigs1             | `-d  <number of significant digits: 6 to 17 (default: 14)>`                 | -d  <number of significant digits: 6 to 17 (default: 14)>                 |
| `report`              | `-t  <report type: basic│stats│dump│dumpvf│dumpc│dumpg (def.: basic│dump)>` | -t  <report type: basic│stats│dump│dumpvf│dumpc│dumpg (def.: basic│dump)> |
