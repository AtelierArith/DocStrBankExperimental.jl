```
EnumerateControls()
```

Find any accessible Aura lighting AuraControl objects and return a set of such, or an empty vector if none are found. Note will also return empty if the Windows 32-bit DLL AURA_SDK.dll is not found (in current directory or in a directory previously set as a valid DLL directory) or if it is not loadable (eg, not 32-bit Windows Julia).
