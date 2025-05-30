```
LinInterp(xvals, xperiod=0.0; require_sorted_input=true) -> LinInterp
```

スカラー値 `xval` を `xvals` のレコードセットに対して一般的な線形補間のための `LinInterp` 構造体を作成します。

[`interp`](@ref) は、`xval` を囲む2つのレコードの重みとインデックスを計算するため、任意のレコードタイプに対して使用可能です。

# 引数:

```
- `xvals::Vector`: 関数が利用可能な x 値。
- `xperiod=0.0`: x 値の周期性 (0.0 は周期的でない)
- `require_sorted_input::Bool=true`: 入力が昇順にソートされていることを確認するため、 
 `false` は任意の順序を許可します (その場合、内部使用のためにソートされます)。
```
