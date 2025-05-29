```
colorder(ct::ConTab, v::AbstractVector{AbstrctString})
```

Make contigency trable with column order as in `v` vector. If item in `v` not present in tab collumn's names - collumn of zeros will be made for that item.

Example 

```
Contingency table:
--------- -------- ----- -------
              B      D    Total 
--------- -------- ----- -------
   G1         1     123     124
   G2         0     124     124
--------- -------- ----- -------
 ID: ColName => id;
```

after `colorder(ct, ["A", "B", "C", "D"])`:

```
Contingency table:
--------- -------- --------- --------- ----- -------
              A         B         C      D    Total 
--------- -------- --------- --------- ----- -------
    G1        0         1         0     123     124
    G2        0         0         0     124     124
--------- -------- --------- --------- ----- -------
ID: ColName => id;
```
