`tryconjugate(p[,goal[,printlevel]])`

このプログラムは、生成子に共役を適用することによって群の発表を簡素化しようとします。アルゴリズムはランダムな数と木探索に依存しているため、再現性はありません。デフォルトでは、プログラムは短い発表が見つかるとすぐに停止します。時には、これが望ましい発表を与えないことがあります。第二の引数`goal`を指定すると、プログラムは`goal`よりも短い長さの発表が見つかるまで停止しません。最後に、第三の引数を指定すると、プログラムが実行するすべての発表のうち、この引数以下の長さのものが表示されます。プログラムの非決定的な性質のため、同じ入力に対して何度も実行することが有用かもしれません。発表の改善に失敗した場合、プログラムは`p`を返します。

```julia-rep1
julia> display_balanced(p)
1: ba=ab
2: dbd=bdb
3: cac=aca
4: bcb=cbc
5: dAca=Acad
6: dcdc=cdcd
7: adad=dada
8: dcDbdc=bdcbdB
9: dcdadc=adcdad
10: adcDad=dcDadc
11: BcccbdcAb=dcbACdddc
julia> p=tryconjugate(p)
Presentation: 4 generators, 11 relators, total length 100
dcD=> Presentation: 4 generators, 10 relators, total length 90
# dcD gives Presentation: 4 generators, 10 relators, total length 90
Presentation: 4 generators, 10 relators, total length 90

julia> p=tryconjugate(p)
Dcd=> Presentation: 4 generators, 10 relators, total length 88
# Dcd gives Presentation: 4 generators, 10 relators, total length 88
Presentation: 4 generators, 10 relators, total length 88

julia> p=tryconjugate(p)
dcD=> Presentation: 4 generators, 10 relators, total length 90
Dbd=> Presentation: 4 generators, 10 relators, total length 96
Aca=> Presentation: 4 generators, 9 relators, total length 84
Presentation: 4 generators, 8 relators, total length 76
# Aca gives Presentation: 4 generators, 8 relators, total length 76
Presentation: 4 generators, 8 relators, total length 76

julia> p=tryconjugate(p)
Bcb=> Presentation: 4 generators, 8 relators, total length 70
# Bcb gives Presentation: 4 generators, 8 relators, total length 70
Presentation: 4 generators, 8 relators, total length 70

julia> p=tryconjugate(p)
Cac=> Presentation: 4 generators, 8 relators, total length 64
# Cac gives Presentation: 4 generators, 8 relators, total length 64
Presentation: 4 generators, 8 relators, total length 64

julia> p=tryconjugate(p)
caC=> Presentation: 4 generators, 8 relators, total length 58
# caC gives Presentation: 4 generators, 8 relators, total length 58
Presentation: 4 generators, 8 relators, total length 58

julia> p=tryconjugate(p)
Cac=> Presentation: 4 generators, 8 relators, total length 64
Cbc=> Presentation: 4 generators, 7 relators, total length 50
# Cbc gives Presentation: 4 generators, 7 relators, total length 50
Presentation: 4 generators, 7 relators, total length 50

julia> p=tryconjugate(p)
cdC=> Presentation: 4 generators, 7 relators, total length 56
Dcd=> Presentation: 4 generators, 7 relators, total length 54
Cac=> Presentation: 4 generators, 7 relators, total length 48
# Cac gives Presentation: 4 generators, 7 relators, total length 48
Presentation: 4 generators, 7 relators, total length 48

julia> p=tryconjugate(p)
caC=> Presentation: 4 generators, 7 relators, total length 50
Cdc=> Presentation: 4 generators, 7 relators, total length 50
Dbd=> Dcd=> Presentation: 4 generators, 7 relators, total length 60
Bab=> Aba=> Aca=> Presentation: 4 generators, 7 relators, total length 46
# Aca gives Presentation: 4 generators, 7 relators, total length 46
Presentation: 4 generators, 7 relators, total length 46

julia> display_balanced(p)
1: db=bd
2: ba=ab
3: cac=aca
4: ada=dad
5: bcb=cbc
6: cdcd=dcdc
7: AdCacd=cAdCac
```
