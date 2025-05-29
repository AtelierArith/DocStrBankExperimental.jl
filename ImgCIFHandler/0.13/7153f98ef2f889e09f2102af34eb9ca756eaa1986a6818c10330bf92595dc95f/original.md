```
scan_frame_from_bin_id(binary_id,cif_block)
```

Return the scan*id, frame*id for the given `binary_id` according to contents of `cif_block`. If `cif_block` contains no scan or frame information,  (nothing,1) is returned. The reverse operation is `bin_id_from_scan_frame`
