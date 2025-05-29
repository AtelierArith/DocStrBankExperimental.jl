```julia
pca_inverse_problem(
    A,
    s,
    k;
    decoder,
    decoder_kwargs,
    out_dic
)

```

pcaの一般的なデコーディング関数。キーワード引数`decoder`を介してデコーディング方法を選択できます。
