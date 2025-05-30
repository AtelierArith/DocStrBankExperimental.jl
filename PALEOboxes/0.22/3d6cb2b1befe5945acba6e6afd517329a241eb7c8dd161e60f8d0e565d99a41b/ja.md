```
ReactionMethod(
    methodfn::Function,
    reaction::AbstractReaction,
    name::String,
    varlists::Tuple{Vararg{AbstractVarList}},
    p, 
    operatorID::Vector{Int64}, 
    domain::AbstractDomain; 
    preparefn = (m, vardata) -> vardata
) -> m::ReactionMethod
```

モデルフレームワークからセットアップ中またはメインループの一部として呼び出される、変数 `varlists` を持つコールバック関数 `methodfn` を定義します。

# フィールド

  * `methodfn`: モデルフレームワークからのコールバック
  * `reaction`: この `ReactionMethod` を作成した反応
  * `name`: 説明的な名前、例えば `methodfn` の名前から生成されたもの
  * `varlists`: 各々が [`VariableReaction`](@ref) のリストを表す VarLists のタプル。対応する変数アクセサ `vardata`（配列のビュー）が `methodfn` コールバックに提供されます。NB: コンパイル時間を短縮するために具体的に型付けされていません。パフォーマンス上重要ではありません。
  * `p`: `methodfn` に必要なデータを格納するための任意の型のコンテキストフィールド。
  * `operatorID`
  * `domain`
  * `preparefn`: preparefn(m::ReactionMethod, vardata::Tuple) -> modified_vardata::Tuple      `vardata` を修正するためにオプションで使用されます。例えばバッファを追加するため。NB: パフォーマンス上重要ではないため具体的に型付けされていません。

# methodfn

`methodfn` コールバックは次のようになります：

```
methodfn(m::ReactionMethod, pars, vardata::Tuple, cellrange::AbstractCellRange, modelctxt)
```

または（パラメータが必要ない場合）：

```
methodfn(m::ReactionMethod, vardata::Tuple, cellrange::AbstractCellRange, modelctxt)
```

引数は次の通りです：

  * `m::ReactionMethod`: コンテキストは `m.reaction::AbstractReaction`（`ReactionMethod` を定義した反応）および `m.p`（`ReactionMethod` 作成時に供給された任意の追加コンテキストフィールド）として利用可能です。
  * `pars`: フィールドとしてパラメータを持つ構造体（現在は `reaction.pars` として定義された ParametersTuple のみ）
  * `vardata`: `varlists` によって定義された [`VariableReaction`](@ref) に対応するドメインデータ配列のビューのコレクションのタプル
  * `cellrange::AbstractCellRange`: 計算するセルの範囲。
  * `modelctxt`:

      * セットアップメソッドの場合、リクエストされたセットアップのタイプを定義する `:setup`、`:initial_value` または `:norm_value`
      * メインループメソッドの場合、レートスロットリングのためのタイムステップ情報を提供する `deltat`。

# preparefn

任意の `preparefn` コールバックを供給することができ、例えば `vardata` のデータ型の知識を必要とするバッファを割り当てたり、高価な計算をキャッシュするために使用されます：

```
preparefn(m::ReactionMethod, vardata::Tuple) -> modified_vardata::Tuple
```

これはモデル配列が割り当てられた後、セットアップの前に呼び出されます。
