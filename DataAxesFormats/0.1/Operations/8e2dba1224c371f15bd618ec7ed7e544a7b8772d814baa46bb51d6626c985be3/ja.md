```
Fraction([; dtype::Type])
```

要素ごとの操作で、すべての要素を合計に対するその分数に変換します。合計がゼロの場合、すべての分数もゼロに設定されます。これは暗黙的に（しかし強制はしません）すべてのエントリ値が正であることを前提としています。

行列の場合、各エントリはその属する列の合計に対する分数になります。ベクトルの場合、各エントリはベクトルの合計に対する分数になります。スカラーの場合、この操作は意味をなさないため、エラーが発生します。

**パラメータ**

`dtype` - デフォルトの出力データ型は、入力データ型の[`float_dtype_for`](@ref)です。
