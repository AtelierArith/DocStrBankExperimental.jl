```
Ephem
```

Ephemeris descriptor. Create with:

```
eph = Ephem(filename)
eph = Ephem([filename1,filename2...])
```

The ephemeris descriptor will be used to access the ephemeris and related   data stored in the specified files.

Because, Julia GC is lazy, you may want to free the memory managed by eph   before you get rid of the reference to eph with:

```
finalize(eph)
```

or after by forcing the GC to run:

```
gc()
```
