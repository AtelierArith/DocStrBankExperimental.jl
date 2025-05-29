```
OofRNG(normrng, slope, fmin, fknee, fsample)
```

`OofRNG` RNGオブジェクトを作成します。これは、`normrng`にガウスRNGジェネレーター（`GaussRNG`を使用）、ノイズのスロープαを`slope`に、最小周波数（最長周期）を`fmin`に、膝周波数とサンプリング周波数を指定する必要があります。これら3つの周波数の測定単位は同じでなければなりません（例：Hz）。

次の例のように、`OofRNG`オブジェクトからサンプルを引き出すには`randoof`を使用します：

```
rng = OofRNG(GaussRNG(), -1.5, 1e-3, 1.0, 1e2)
print([randoof(rng) for i in 1:4])
```
