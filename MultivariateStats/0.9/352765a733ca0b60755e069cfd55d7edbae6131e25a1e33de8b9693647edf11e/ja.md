```
fit(MDS, X; kwargs...)
```

`X`ポイントの埋め込みを古典的多次元尺度法（MDS）によって計算します。必要なキーワード引数`distances`を介して指定された2つの呼び出しオプションがあります：

```
mds = fit(MDS, X; distances=false, maxoutdim=size(X,1)-1)
```

ここで`X`はデータ行列です。`X`の列のペア間の距離はユークリッドノルムを使用して計算されます。これは`X`に対してPCAを実行することと同等です。

```
mds = fit(MDS, D; distances=true, maxoutdim=size(D,1)-1)
```

ここで`D`はポイント間の距離の対称行列`D`です。
