```
 psyscl = psfeedback(psys, K, (inp, out); negative = false)
```

与えられた周期的システム `psys` と入力ベクトル `u` および出力ベクトル `y`、周期的出力フィードバックゲイン `K(t)` に対して、メモリーレス出力フィードバック `u[inp] = K(t)*y[out] + v` に対応する閉ループ周期的システム `psyscl` を構築します。ここで、`inp` と `out` はインデックス、インデックスのベクトル、インデックス範囲、`:` またはそれらの任意の組み合わせです。指定できるのは異なるインデックスのみです。`negative = true` の場合、負の psfeedback `u[inp] = -K(t)*y[out] + v` が使用されます。
