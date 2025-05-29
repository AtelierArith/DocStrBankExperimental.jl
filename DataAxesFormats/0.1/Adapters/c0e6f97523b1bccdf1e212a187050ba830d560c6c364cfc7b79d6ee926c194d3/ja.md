```
adapter(
    computation::Function,
    daf::DafWriter;
    input_axes::Maybe{ViewAxes} = nothing,
    input_data::Maybe{ViewData} = nothing,
    capture = MemoryDaf,
    output_axes::Maybe{ViewAxes} = nothing,
    output_data::Maybe{ViewData} = nothing,
    empty::Maybe{EmptyData} = nothing,
    relayout::Bool = true,
    overwrite::Bool = false,
)::Any
```

`daf`データのビューに対して`computation`を呼び出し、結果を返します。結果のビューを基本の`daf`データにコピーします。

`computation`を実行したい`Daf`データがある場合、名前の不一致に対処する必要があります。つまり、`computation`の入力および出力データプロパティの名前が、データで使用されている名前と異なる場合があります。さらに、計算されたデータプロパティのサブセットのみを興味がある場合があり、無関係なプロパティでデータセットが汚染されるのを避けたいことがあります。

これらの問題に対処するために、`Daf`データに計算を適用するための一般的な慣用句は、次のように`adapter`を使用することです。

  * `input_axes`と`input_data`を使用して、`computation`が期待する名前の下でデータプロパティを提示する（読み取り専用の）データのビューを作成します。`computation`が[`@computation`](@ref)で注釈されている場合、その[`Contract`](@ref)が明示的に文書化されるため、何を提供すべきか正確に知ることができます。
  * この読み取り専用ビューを空の`capture`書き込み可能データセット（デフォルトでは[`MemoryDaf`](@ref)）とチェーンし、結果を`computation`に「適応された」データセットとして渡します。
  * `computation`が完了したら、`output_axes`と`output_data`を使用して出力のビューを作成し、このサブセットを元の`daf`データセットにコピーします（[`copy_all!`](@ref)、`empty`、`relayout`（デフォルト：`true`）、および`overwrite`（デフォルト：`false`）を使用）。

通常、コードは次のようになります。

```
daf = ... # 計算を実行したい入力`Daf`データ。

# ここで`daf`は計算の入力を含んでいますが、異なる名前の可能性があります。

result = adapter(
    daf;                                   # 計算を適用したいDafデータセット。
    input_axes = ..., input_data = ...,    # 計算に提供する方法と内容。
    output_axes = ..., output_data = ...,  # 計算の出力として戻す方法と内容。
    empty = ...,                           # 入力ビューがいくつかの軸のサブセットを指定する場合。
) do adapted                   # 計算に渡すことができる書き込み可能な適応データ。
    computation(adapted, ...)  # 実際に計算を行います。
    return ...                 # `daf`の外にある追加の結果。
end

# ここで`daf`は`adapter`で指定された特定の名前変更された出力を含み、
# 追加の非`daf`データ`result`にもアクセスできます。
```

この慣用句により、[`@computation`](@ref)関数は入力と出力のために明確な一般名を使用し、より具体的な名前を使用する任意のデータセットに適用することができます。同じ計算を異なるパラメータ値で呼び出し、異なる名前の同じデータセットに異なる結果を保存することもできます。
