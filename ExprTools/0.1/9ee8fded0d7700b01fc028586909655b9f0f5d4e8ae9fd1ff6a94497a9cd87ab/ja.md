```
signature(m::Method) -> Dict{Symbol,Any}
```

メソッドのシグネチャの式を、さまざまなコンポーネントに分解して見つけます。これには以下が含まれます：

  * `:name`: 関数の名前
  * `:params`: コンストラクタで定義されたパラメトリック型
  * `:args`: 関数の位置引数
  * `:whereparams`: Whereパラメータ

上記のすべてのコンポーネントは、関数定義に存在しない場合、返される辞書に含まれないことがあります。

サポートされている制限：

  * `:kwargs`: 関数のキーワード引数。デフォルト値や型制約ではなく、名前のみが含まれます。

サポートされていない：

  * `:rtype`: 関数の戻り値の型
  * `:body`: 関数の本体
  * `:head`: 関数定義の式のヘッド（`:function`、`:(=)`、`:(->)`）

より完全なカバレッジを得るには、[`splitdef`](@ref)を[`CodeTracking.definition`](https://github.com/timholy/CodeTracking.jl)と一緒に使用することを検討してください。

`signature`によって返されるコンポーネントの辞書は、[`splitdef`](@ref)によって返されるものと一致し、`：body`コンポーネントを除いて、[`combinedef`](@ref)によって要求されるすべてを含みます。

# キーワード

  * `extra_hygiene=false`: `true`に設定すると、`UnionAll`内の`TypeVar`に名前の衛生を強制し、`gensym`を介して一意の名前で再生成します。これは、スコープが漏れないように設計されているため、実際には必要ないはずです。しかし、関数の型変数と衝突した場合に漏れるという長年の[juliaバグ](https://github.com/JuliaLang/julia/issues/39876)があります。
