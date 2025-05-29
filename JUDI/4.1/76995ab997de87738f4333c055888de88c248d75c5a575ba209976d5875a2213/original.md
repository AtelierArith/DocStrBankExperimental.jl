```
judiVector
    nsrc::Integer
    geometry::Geometry
    data::Vector
```

Abstract vector for seismic data. This vector-like structure contains the geometry and data for either
receiver data (shot records) or source data (wavelets).

# Constructors

Construct vector from `Geometry` structure and cell array of shot records or wavelets. The `data` keyword
can also be a single (non-cell) array, in which case the data is the same for all source positions:

```
judiVector(geometry, data)
```

Construct vector for observed data from `SeisBlock`. `segy_depth_key` is the `SegyIO` keyword 
that contains the receiver depth coordinate:

```
judiVector(SeisBlock; segy_depth_key="RecGroupElevation")
```

Construct vector for observed data from out-of-core data container of type `SeisCon`:

```
judiVector(SeisCon; segy_depth_key="RecGroupElevation")
```

# Examples

(1) Construct data vector from `Geometry` structure and a cell array of shot records:

```
dobs = judiVector(rec_geometry, shot_records)
```

(2) Construct data vector for a seismic wavelet (can be either cell arrays of individual
wavelets or a single wavelet as an array):

```
q = judiVector(src_geometry, wavelet)
```

(3) Construct data vector from `SeisBlock` object:

```
using SegyIO
seis_block = segy_read("test_file.segy")
dobs = judiVector(seis_block; segy_depth_key="RecGroupElevation")
```

(4) Construct out-of-core data vector from `SeisCon` object (for large SEG-Y files):

```
using SegyIO
seis_container = segy_scan("/path/to/data/directory","filenames",["GroupX","GroupY","RecGroupElevation","SourceDepth","dt"])
dobs = judiVector(seis_container; segy_depth_key="RecGroupElevation")
```
