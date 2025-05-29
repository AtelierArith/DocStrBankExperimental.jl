```julia
msopck(
;
    setup,
    input,
    output,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

MSOPCK is a command-line program that converts attitude data provided in a text file as UTC, SCLK, or ET-tagged quaternions, Euler angles, or matrices, optionally accompanied by angular velocities, into a type 1, 2, or 3 SPICE C-kernel.
