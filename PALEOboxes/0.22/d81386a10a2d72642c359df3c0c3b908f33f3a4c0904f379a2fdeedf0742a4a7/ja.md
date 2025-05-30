```
LinInterp(xvals, xperiod=0.0; require_sorted_input=true) -> LinInterp
```

`xvals`のレコードセットに対してスカラー値`xval`のための一般的な線形補間の`LinInterp`構造体を作成します。

[`interp`](@ref)は、`xval`を囲む2つのレコードの重みとインデックスを計算するため、任意のレコードタイプに使用できます。

# 引数:

```
- `xvals::Vector`: 関数が利用可能なx値。
- `xperiod=0.0`: x値の周期性（周期的でない場合は0.0）
- `require_sorted_input::Bool=true`: 入力が昇順にソートされていることを確認するため、 
 `false`は任意の順序を許可します（その場合、内部使用のためにソートされます）。
```
