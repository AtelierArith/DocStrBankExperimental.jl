```
XPRS_MIPABSSTOP
```

分岐限定法: ツリー探索を続けるかどうかを決定する絶対許容誤差。(double)

|`MIPOBJVAL - BESTBOUND`| `<=` `MIPABSSTOP` の場合に終了します。ここで、MIPOBJVALは最良解の目的関数の値であり、BESTBOUNDは現在の最良解の境界です。たとえば、MIP解が見つかり、オプティマイザが最適解から100以内であることを保証できる場合、`MIPABSSTOP`を100に設定します。

デフォルト値: `0.0`

範囲: [-INF,+INF]
