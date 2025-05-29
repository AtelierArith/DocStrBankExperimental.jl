`simplify(p [,tries])`

simplify  the  presentation  `p`.  We  have  found heuristics which make it somewhat  efficient, but the algorithm depends  on random numbers so is not reproducible.  The main  idea is  to rotate  relators between  calls to the basic  `GroupPresentations.Go` function. By default 100 such rotations are tried (unless  the  presentation  is  so  small  that  less rotations exhaust all possible  ones), but the actual number tried  can be controlled by giving a second  parameter `tries` to the function. Another useful tool to deal with presentations is `tryconjugate`.

```julia-rep1
julia> display_balanced(p)
1: ab=ba
2: dbd=bdb
3: bcb=cbc
4: cac=aca
5: adca=cadc
6: dcdc=cdcd
7: adad=dada
8: Dbdcbd=cDbdcb
9: adcDad=dcDadc
10: dcdadc=adcdad
11: dcabdcbda=adbcbadcb
12: caCbdcbad=bdcbadBcb
13: cbDadcbad=bDadcbadc
14: cdAbCadBc=bdcAbCdBa
15: cdCbdcabdc=bdcbadcdaD
16: DDBcccbdcAb=cAbCdcBCddc
17: CdaBdbAdcbCad=abdcAbDadBCbb
18: bdbcabdcAADAdBDa=cbadcbDadcBDABDb
19: CbdbadcDbbdCbDDadcBCDAdBCDbdaDCDbdcbadcBCDAdBCDBBdacDbdccb=abdbcabdcAdcbCDDBCDABDABDbbdcbDadcbCDAdBCabDACbdBadcaDbAdd

julia> simplify(p)
Presentation: 4 generators, 18 relators, total length 304
Presentation: 4 generators, 18 relators, total length 284
Presentation: 4 generators, 17 relators, total length 264
Presentation: 4 generators, 16 relators, total length 256
Presentation: 4 generators, 15 relators, total length 244
Presentation: 4 generators, 15 relators, total length 240
Presentation: 4 generators, 15 relators, total length 226
Presentation: 4 generators, 15 relators, total length 196
Presentation: 4 generators, 15 relators, total length 178
Presentation: 4 generators, 15 relators, total length 172
Presentation: 4 generators, 14 relators, total length 158

julia> display_balanced(p)
1: ab=ba
2: dbd=bdb
3: bcb=cbc
4: cac=aca
5: adAc=cadA
6: dcdc=cdcd
7: adad=dada
8: CdBcbd=bCdBcb
9: adcDad=dcDadc
10: dcdadc=adcdad
11: cbdcbdc=dcbdcbd
12: dcbadcbda=adcbcadcb
13: cbCDadcab=DadcbadcD
14: caDCbdBcADbda=bDBaDbADcbadc
```
