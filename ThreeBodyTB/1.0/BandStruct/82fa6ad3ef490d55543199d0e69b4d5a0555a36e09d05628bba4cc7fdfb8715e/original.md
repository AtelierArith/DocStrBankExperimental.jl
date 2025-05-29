```
function plot_bandstr(h::tb_crys; kpath, names = missing, proj_types=missing, proj_orbs = missing, proj_nums=missing)
```

Plot the band structure of a `tb_crys` object. Can also perform a projected band structure if you specify at least one of `proj_types`, `proj_orbs`, `proj_nums`.

k-path specified by a kpath array and names.

Must do scf calculation before plotting.

# Arguments

  * `h::tb_crys` - The tight-biding object we want to plot bands from. Only required argument.
  * `kpath=[0.5 0 0 ; 0 0 0; 0.5 0.5 0.5; 0 0.5 0.5; 0 0 0 ;0 0 0.5]` - `nk` × 3 array k-point path (high symmetry points).
  * `npts=30,` - number of points between high-symmetry k-points.
  * `names=missing` - `nk` string array. Names of the high-symmetry k-points
  * `proj_types=missing` - types to project onto. Either `proj_types="H"` or `proj_types=["H", "O"]` are valid.
  * `proj_orbs=missing` - orbitals to project onto. either `proj_orbs=:s` or `proj_orbs=[:s, :p]`.
  * `proj_nums=missing` - atom numbers to project onto. Either `proj_nums=1` or `proj_nums=[1, 2]`
  * `efermi=missing` - allows you to specify fermi energy. Default is to take from `h`
  * `color="blue"` - specify line color
  * `MarkerSize=missing"` - specify markersize
  * `yrange=missing"` - specify y-range. e.g. `yrange=[-0.7, 0.3]`
  * `plot_hk=false` - plot things besides the normal band structure. Can be one of `:Seig, :Heig, :Hreal, :Himag, :Sreal, :Simag` to plot H or S eigvals or components. Primarily for debugging.
  * `align="vbm"` - default or `"valence"` is to align valence band max to zero energy. Can also be `"min"`, which aligns on the minimum eigenvalue, or `"fermi"` or `"ef"`, which align on the Fermi level,
  * `clear_pervious=true` - clears the plot before adding new stuff.
  * `do_display=true` - display the plot. If `false`, can be used with display-less nodes. You can still use `savefig` from `Plots` to produce saved images.
