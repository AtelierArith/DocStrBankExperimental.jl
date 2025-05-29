```
Oof2RNG(normrng, fmin, fknee, fsample)
```

`Oof2RNG` RNGオブジェクトを作成します。これは、`normrng`にガウスRNGジェネレーター（`GaussRNG`を使用）を必要とし、最小周波数（最長周期）`fmin`、膝周波数`fknee`、およびサンプリング周波数`fsample`を必要とします。これらの3つの周波数の測定単位は同じでなければなりません（例：Hz）。

次の例のように、`Oof2RNG`オブジェクトからサンプルを引き出すには、`randoof2`を使用します：

```
rng = Oof2RNG(GaussRNG(), 1e-3, 1.0, 1e2)
print([randoof2(rng) for i in 1:4])
```
