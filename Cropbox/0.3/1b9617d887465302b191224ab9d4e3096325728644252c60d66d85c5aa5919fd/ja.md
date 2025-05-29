```
simulate([f,] S[, layout, [configs]]; <keyword arguments>) -> DataFrame
```

与えられた構成でシステム `S` のインスタンスを作成することによってシミュレーションを実行し、DataFrame 形式の出力を生成します。`layout` には出力に保存される変数のリストが含まれています。単一のシミュレーションのレイアウトは、キーワード引数として配置されたレイアウト引数で指定できます。`configs` には、各シミュレーションの実行のための構成のリストが含まれています。シミュレーションの実行回数の合計は `configs` のサイズに等しくなります。単一の構成の場合、`config` キーワード引数が好まれることがあります。オプションのコールバック関数 `f` は、出力形式の詳細な制御のために `snatch` 引数を指定するための do-block 構文を許可します。

参照: [`instance`](@ref), [`@config`](@ref)

# 引数

  * `S::Type{<:System}`: シミュレーションされるシステムのタイプ。
  * `layout::Vector`: 名前付きタプル `(; base, index, target, meta)` での出力レイアウト定義のリスト。
  * `configs::Vector`: 複数のシミュレーション実行を定義するための構成のリスト。

# キーワード引数

## レイアウト

  * `base=nothing`: `index` と `target` が populated されるベースシステム; デフォルトは `S` のインスタンスにフォールバックします。
  * `index=nothing`: 出力のインデックス列を構築するための変数; デフォルトは `context.clock.time` にフォールバックします。
  * `target=nothing`: 出力の非インデックス列を構築するための変数; デフォルトはルートインスタンスのほとんどの変数を含みます。
  * `meta=nothing`: 出力にメタデータとして含める構成内のシステムの名前。

## 構成

  * `config=()`: システムの単一の構成、または複数の構成のためのベース（`configs` と一緒に使用される場合）。
  * `configs=[]`: システムの複数の構成。
  * `seed=nothing`: 各シミュレーション実行をリセットするためのランダムシード。

## 進行状況

  * `stop=nothing`: インスタンスの更新を呼び出す前にチェックされる条件; デフォルトは更新なしで停止します。
  * `snap=nothing`: 現在の更新のスナップショットが出力に保存されるかどうかを決定するためにチェックされる条件; デフォルトはすべての更新をスナップします。
  * `snatch=nothing`: 中間出力を修正するためのコールバック; 現在の更新から収集された DataFrame `D` とシステム `s` のインスタンスが提供されます。
  * `verbose=true`: 進行状況バーを表示します。

## 形式

  * `nounit=false`: 出力から単位を削除します。
  * `long=false`: 出力テーブルをワイド形式からロング形式に変換します。

# 例

```julia-repl
julia> @system S(Controller) begin
           a => 1 ~ preserve(parameter)
           b(a) ~ accumulate
       end;

julia> simulate(S; stop=1)
2×3 DataFrame
 Row │ time       a        b
     │ Quantity…  Float64  Float64
─────┼─────────────────────────────
   1 │    0.0 hr      1.0      0.0
   2 │    1.0 hr      1.0      1.0
```
