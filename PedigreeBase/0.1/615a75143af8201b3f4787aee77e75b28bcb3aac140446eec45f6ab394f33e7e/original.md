```
c = get_inbupg_code(s, d, f)
c = get_inbupg_code(pedlist, f)
```

Returns the "inb/upg code" out of sire ID `s`, dam ID `d`, and a list of inbreeding coefficient `f`. Instead of single ID, you can provide lists of sires and dams (unified list `pedlist` or separate lists `s` and `d`) to obtain the code for all individuals. The code is integer, and it is useful only for the BLUPF90 programs.
