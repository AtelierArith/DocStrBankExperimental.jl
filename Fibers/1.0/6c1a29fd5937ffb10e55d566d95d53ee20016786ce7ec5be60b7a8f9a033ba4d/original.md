```
mri_filename(fstring::String, checkdisk::Bool=true)
```

Return a valid file name, file stem, and file extension, given a string `fstring` that can be either a file name or a file stem.

Valid extensions are: mgh, mgz, nii, nii.gz. Thus a file name is expected to have the form stem.{mgh, mgz, nii, nii.gz}.

If `fstring` is a file name, then the stem and extension are determined from `fstring`.

If `fstring` is a file stem and `checkdisk` is true (default), then the file name and extension are determined by searching for a file on disk named `fstring`.{mgh, mgz, nii, nii.gz}, where the possible extensions are searched for in this order. If no such file is found, then empty strings are returned.
