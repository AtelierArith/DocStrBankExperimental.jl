```
netrc!(username, password)
```

Writes/updates a .netrc file for ICESat-2 and GEDI downloads. A .netrc is a plaintext file containing your username and password for NASA EarthData and DAACs, and can be automatically used by Julia using `Downloads` and tools like `wget`, `curl` among others.
