```
XPRS_MIPRELSTOP
```

分岐限定法: これは分岐限定法の木探索がいつ終了するかを決定します。(double)

分岐限定法の木探索は次の場合に停止します: |`MIPOBJVAL - BESTBOUND`| `<=` `MIPRELSTOP` x max(|`BESTBOUND`|,|`MIPOBJVAL`|) ここで、MIPOBJVALは最良解の目的関数の値であり、BESTBOUNDは現在の最良解の境界です。例えば、MIP解が見つかり、最適解から5以内であることが保証される場合に木探索を停止するには、`MIPRELSTOP`を0.05に設定します。

デフォルト値: `0.0001`

範囲: [-INF,+INF]
