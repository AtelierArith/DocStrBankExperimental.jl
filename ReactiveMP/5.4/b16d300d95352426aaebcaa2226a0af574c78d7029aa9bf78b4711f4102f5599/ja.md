BIFMノードは、状態空間モデルの代替として使用できるノードです。効率的な推論を行うために、時間スライスのすべての因子を含んでいます。このノードは、効率的な推論のためにBIFMHelperノードと一緒に使用する必要があります。

```julia
out ~ BIFM(in, zprev, znext)
```

インターフェース:

1. out - BIFMノードの潜在出力（観測）
2. in - BIFMノードの潜在入力
3. zprev - BIFMノードの前の潜在状態
4. znext - BIFMノードの次の潜在状態

*注: 推論を行う際は、まず周辺分布（z、out、inの順）にサブスクライブし、その後自由エネルギースコア関数にサブスクライブしてください。*

## 例

```julia
# 事前分布を設定
z_prior ~ MvNormalMeanPrecision(zeros(latent_dim), diagm(ones(latent_dim)))
z_tmp   ~ BIFMHelper(z_prior)

# 最後の/前の隠れ状態を更新
z_prev = z_tmp

# 観測をループ
for i in 1:nr_samples

    # 入力を確率変数として指定
    u[i]   ~ MvNormalMeanPrecision(μu, Wu)

    # 観測を指定
    xt[i]  ~ BIFM(u[i], z_prev, z[i]) where { meta = BIFMMeta(A, B, C) }
    x[i]   ~ MvNormalMeanPrecision(xt[i], Wx)
    
    # 最後の/前の隠れ状態を更新
    z_prev = z[i]

end
```
