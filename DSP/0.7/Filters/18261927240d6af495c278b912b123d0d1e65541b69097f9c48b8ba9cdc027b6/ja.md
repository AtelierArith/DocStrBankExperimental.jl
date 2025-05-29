```
iirnotch(Wn, bandwidth[; fs])
```

周波数 `Wn` で帯域幅 `bandwidth` の二次デジタル IIR ノッチフィルタ [^Orfandis]。`fs` が指定されていない場合、`Wn` は半周期/サンプルの正規化周波数として解釈されます。

[^Orfandis]: Orfanidis, S. J. (1996). Introduction to signal processing. Englewood Cliffs, N.J: Prentice Hall, p. 370.
