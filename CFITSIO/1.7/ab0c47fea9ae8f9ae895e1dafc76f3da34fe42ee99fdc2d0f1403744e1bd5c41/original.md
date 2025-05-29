```
fits_copy_file(fin::FITSFile, fout::FITSFile, previous::Bool, current::Bool, following::Bool)
```

Copy all or a part of the HDUs from the input file `fin`, and append them to the output file `fout`. The flags `previous`, `current` and `following` specify which HDUs are to be copied.

  * If `previous` is true, all the HDUs prior to the current input HDU are copied.
  * If `current` is true, the current input HDU is copied.
  * If `following` is true, all the HDUs following the current input HDU are copied.

These flags may be combined, so if all are set to `true` then all the HDUs are copied from `fin` to `fout`.

On exit, the input is unchanged, and the last HDU in the output is set as the current HDU.
