```
AICode(code::AbstractString; auto_eval::Bool=true, safe_eval::Bool=false, 
skip_unsafe::Bool=false, capture_stdout::Bool=true, verbose::Bool=false,
prefix::AbstractString="", suffix::AbstractString="", remove_tests::Bool=false, execution_timeout::Int = 60)

AICode(msg::AIMessage; auto_eval::Bool=true, safe_eval::Bool=false, 
skip_unsafe::Bool=false, skip_invalid::Bool=false, capture_stdout::Bool=true,
verbose::Bool=false, prefix::AbstractString="", suffix::AbstractString="", remove_tests::Bool=false, execution_timeout::Int = 60)
```

AIモデルから受け取ったコードブロックを表す可変構造体で、自動解析、実行、出力/エラーキャプチャ機能を備えています。

文字列でインスタンス化すると、`AICode`オブジェクトは自動的にコードパーサーと実行者（`PromptingTools.eval!()`を介して）を実行し、標準出力（`stdout`）やエラーをキャプチャします。この構造体は、プログラム的にJuliaコードスニペットを処理および評価するのに便利です。

参照: `PromptingTools.extract_code_blocks`, `PromptingTools.eval!`

# ワークフロー

  * `cb::AICode`が評価されるまで、`cb.success`は`nothing`に設定されます（他のすべてのフィールドも同様です）。
  * `cb.code`のテキストが解析され（`cb.expression`に保存されます）、評価されます。
  * 評価された式の出力が`cb.output`にキャプチャされます。
  * 評価された式からの`stdout`出力（例：`println`からの出力）が`cb.stdout`にキャプチャされます。
  * 評価中にエラーが発生した場合、それは`cb.error`に保存されます。
  * エラーなしで成功裏に評価された後、`cb.success`は`true`に設定されます。そうでない場合は`false`に設定され、`cb.error`を調べて理由を理解できます。

# プロパティ

  * `code::AbstractString`: 解析および実行されるコードの生の文字列。
  * `expression`: 解析されたJulia式（`code`を解析した後に設定されます）。
  * `stdout`: コードの実行からキャプチャされた標準出力。
  * `output`: コードブロックの評価結果。
  * `success::Union{Nothing, Bool}`: コードブロックが成功裏に実行されたか（`true`）、失敗したか（`false`）、またはまだ評価されていないか（`nothing`）を示します。
  * `error::Union{Nothing, Exception}`: コードブロックの実行中に発生した例外。

# キーワード引数

  * `auto_eval::Bool`: `true`に設定すると、インスタンス化時にコードブロックが自動的に解析および評価されます。デフォルトは`true`です。
  * `safe_eval::Bool`: `true`に設定すると、コードブロックはパッケージ操作（例：新しいパッケージのインストール）や不足しているインポートをチェックし、その後、特注のスクラッチモジュール内でコードを評価します。これは、評価がユーザー定義の変数やグローバル状態を変更しないことを保証するためです。デフォルトは`false`です。
  * `skip_unsafe::Bool`: `true`に設定すると、安全でないと見なされるコードブロック内の行をスキップします（例：`Pkg`操作）。デフォルトは`false`です。
  * `skip_invalid::Bool`: `true`に設定すると、解析すらできないコードブロックをスキップします。デフォルトは`false`です。
  * `verbose::Bool`: `true`に設定すると、安全でないためにスキップされた行を出力します。デフォルトは`false`です。
  * `capture_stdout::Bool`: `true`に設定すると、`cb.stdout`に任意のstdout出力（例：テストの失敗）をキャプチャします。デフォルトは`true`です。
  * `prefix::AbstractString`: 解析および評価の前にコードブロックに追加される文字列。追加のコード定義や必要なインポートを追加するのに便利です。デフォルトは空文字列です。
  * `suffix::AbstractString`: 解析および評価の前にコードブロックに追加される文字列。テストが通過するか、例が実行されるかを確認するのに便利です。デフォルトは空文字列です。
  * `remove_tests::Bool`: `true`に設定すると、解析および評価の前にコードブロックから任意の`@test`または`@testset`マクロを削除します。デフォルトは`false`です。
  * `execution_timeout::Int`: コードブロックの実行に許可される最大時間（秒単位）。デフォルトは60秒です。

# メソッド

  * `Base.isvalid(cb::AICode)`: コードブロックが成功裏に実行されたかどうかを確認します。`cb.success == true`の場合は`true`を返します。

# 例

```julia
code = AICode("println("Hello, World!")") # コードを自動的に解析および評価し、出力とエラーをキャプチャします。
isvalid(code) # 出力: true
code.stdout # 出力: "Hello, World!
"
```

デフォルトでは「安全に」評価しようとします（例：カスタムモジュール内で、ユーザー変数を変更しないように）。これを避けるには、`save_eval=false`を使用します：

```julia
code = AICode("new_variable = 1"; safe_eval=false)
isvalid(code) # 出力: true
new_variable # 出力: 1
```

AIMessageに直接AICodeを呼び出すこともでき、Juliaコードブロックを抽出し、それらを連結して評価します：

```julia
msg = aigenerate("In Julia, how do you create a vector of 10 random numbers?")
code = AICode(msg)
# 出力: AICode(Success: True, Parsed: True, Evaluated: True, Error Caught: N/A, StdOut: True, Code: 2 Lines)

# コードを表示
code.code |> println
# 出力: 
# numbers = rand(10)
# numbers = rand(1:100, 10)

# またはクリップボードにコピー
code.code |> clipboard

# または現在のモジュール（=Main）で実行
eval(code.expression)
```
