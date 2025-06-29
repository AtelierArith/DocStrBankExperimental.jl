```
(; ll, e, S, Sᵪ, K) = correct!(kf::AbstractKalmanFilter, u, y, p = parameters(kf), t::Integer = index(kf), R2)
```

カルマンフィルタの補正ステップは、対数尤度 `ll` と予測誤差 `e` だけでなく、出力の共分散 `S`、そのコレスキー因子 `Sᵪ`、およびカルマンゲイン `K` も返します。

`kf` に格納されている `R2` が関数 `R2(x, u, p, t)` の場合、この関数は補正が行われる *前* の状態で評価されます。フィルタオブジェクトに格納されている測定ノイズ共分散行列 `R2` は、引数 `R2` を渡すことでオプションで上書きできます。この場合、`R2` は行列でなければなりません。

# 拡張ヘルプ

異なるセンサーに対して別々の測定更新を行うには、[ドキュメントの「測定モデル」](@ref measurement_models)を参照してください。
