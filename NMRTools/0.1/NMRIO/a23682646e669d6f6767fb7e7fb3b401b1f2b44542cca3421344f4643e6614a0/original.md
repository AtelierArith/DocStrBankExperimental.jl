```
loadnmr(filename, experimentfolder=nothing)
```

Main function for loading NMR data. `experimentfolder` contains the path to an experiment directory, for identification of metadata, if the filename is not directly within an experiment.

Returns an `NMRData` structure, or throws an `NMRToolsError` is there is a problem.

# Examples

nmrPipe import:

```julia
loadnmr("exampledata/1D_1H/1/test.ft1");
loadnmr("exampledata/1D_19F/1/test.ft1");
loadnmr("exampledata/2D_HN/1/test.ft2");
loadnmr("exampledata/pseudo2D_XSTE/1/test.ft1");
loadnmr("exampledata/pseudo3D_HN_R2/1/ft/test%03d.ft2");
```

Bruker pdata import:

```julia
loadnmr("exampledata/1D_19F/1");
loadnmr("exampledata/1D_19F/1/");
loadnmr("exampledata/1D_19F/1/pdata/1");
loadnmr("exampledata/1D_19F/1/pdata/1/");
```

ucsf (Sparky) import:

```julia
loadnmr("exampledata/2D_HN/1/hmqc.ucsf");
loadnmr("exampledata/1D_19F/1/");
loadnmr("exampledata/1D_19F/1/pdata/1");
loadnmr("exampledata/1D_19F/1/pdata/1/");
```
