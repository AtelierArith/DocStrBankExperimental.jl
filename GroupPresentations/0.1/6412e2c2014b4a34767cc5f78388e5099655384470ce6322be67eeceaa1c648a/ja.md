`simplify(p [,tries])`

プレゼンテーション `p` を簡素化します。いくつかの効率的なヒューリスティックを見つけましたが、アルゴリズムはランダムな数に依存しているため再現性はありません。主なアイデアは、基本的な `GroupPresentations.Go` 関数への呼び出しの間に関係を回転させることです。デフォルトでは、100回の回転が試みられます（プレゼンテーションが非常に小さい場合は、回転がすべての可能なものを使い果たすまで少なくなります）が、実際に試みる回数は、関数に2番目のパラメータ `tries` を与えることで制御できます。プレゼンテーションを扱うためのもう一つの便利なツールは `tryconjugate` です。

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
