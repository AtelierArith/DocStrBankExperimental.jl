```
function dos_realspace(tbc; direction=3, grid=missing, smearing=0.005, npts=missing, do_display=true, use_sym=false, energy_grid=100, width=missing, energy_lims=missing, scissors_shift=0.0, scissors_shift_atoms=[])
```

Makes an atom and spatially resoloved DOS-style plot. Along `direction=1,2,3` (lattice vector 1,2,3) the atoms are plotted, using transparancy to denote DOS amplitude. Try it out to see. Potentially useful for interfaces. Example usage: `c = makecrys([8.0 0 0; 0 8.0 0; 0 0 10.0], [0 0 0; 0 0 0.5], [:Li, :Cl]) #quasi 1D LiCl chain` `en, tbc, flag = scf_energy(c*[1,1,10])                                   #ten unit cells` `dos_realspace(tbc, direction=3)`

Adjust the `energy_grid` and `width` to adjust plotting parameters. Scissors shift in energy unit to certain atoms will add scissors shift to open band gaps is desired.
