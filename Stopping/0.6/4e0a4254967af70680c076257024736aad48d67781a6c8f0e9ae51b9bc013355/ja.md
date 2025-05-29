モジュール停止:

## 目的

反復ソルバーにおける停止基準の均一化を容易にするツール。

ソルバーが最適化モデルに対して呼び出されると、4つの結果が発生する可能性があります。

1. おおよその解が得られ、問題は解決されたと見なされる
2. 問題が解決不可能であると宣言される（無限大、不適合など）
3. 解を計算するための最大利用可能リソースが不十分である
4. アルゴリズム依存の失敗が発生する

このツールは上記の最初の3項目を容易にします。次のような型を定義します。

```
mutable struct GenericStopping <: AbstractStopping
    problem       :: Any          # 問題の任意のインスタンス
    meta          :: AbstractStoppingMeta # 使用されるパラメータを含む
    current_state :: AbstractState        # 現在の状態
```

`StoppingMeta`はデフォルトの許容誤差、最大リソースなどを提供し、結果に関する（ブール）情報も提供します。

### あなたの方法での停止

`GenericStopping`（`GenericState`を使用）では、停止基準を処理するための完全な構造を提供します。次に、問題の構造に応じて、状態を再定義し、問題に特有のいくつかの関数を再定義することで、新しい停止を特化できます。

`NLPStopping`、`NLPAtX`、`LS_Stopping`、`OneDAtX`も参照してください。

これらの例では、関数`optimality_residual`が最適性条件の残差を計算し、型の追加属性となります。

## 関数

このツールは2つの主要な関数を提供します。

  * `start!(stp :: AbstractStopping)`は、開始点での時間と許容誤差を初期化し、初期推測が最適であるかどうかを確認します。
  * `stop!(stp :: AbstractStopping)`は、現在の推測の最適性とシステムの失敗（例えば無限大）および最大リソース（関数の評価回数、経過時間など）を確認します。

停止は、状態によって提供された情報を使用してその関数を評価します。両者間の通信は、次の関数を通じて行うことができます。

  * `update_and_start!(stp :: AbstractStopping; kwargs...)`は、kwargsとして提供された情報で状態を更新し、その後start!を呼び出します。
  * `update_and_stop!(stp :: AbstractStopping; kwargs...)`は、kwargsとして提供された情報で状態を更新し、その後stop!を呼び出します。
  * `fill_in!(stp :: AbstractStopping, x :: T)`は、停止関数を正しく評価するために必要なすべての情報で状態を埋める関数です。これは、ユーザーが状態内のアルゴリズムによって提供された情報を信頼しない場合に役立つことがあります。
  * `reinit!(stp :: AbstractStopping)`は、別の呼び出しのために停止のエントリを再初期化します。
