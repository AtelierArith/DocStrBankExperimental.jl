データ REPL（'}'を通じてアクセス可能）で使用できるコマンド。

`ReplCmd` は以下を持たなければなりません：

  * `name`、コマンドキーワードを指定するシンボル。
  * `trigger`、コマンドトリガーとして使用される文字列（デフォルトは `String(name)`）。
  * `description`、機能の簡単な概要を示す `string` または `display` 可能なオブジェクト。
  * `execute`、サブ ReplCmd のリスト、またはコマンドのアクションを実行する関数。関数は単一の引数を受け取る必要があり、コマンドの残りを `AbstractString` として受け取ります（例えば、'cmd arg1 arg2' は "arg1 arg2" で execute 関数を呼び出します）。

# コンストラクタ

```julia
ReplCmd{name::Symbol}(trigger::String, description::Any, execute::Function)
ReplCmd{name::Symbol}(description::Any, execute::Function)
ReplCmd(name::Union{Symbol, String}, trigger::String, description::Any, execute::Function)
ReplCmd(name::Union{Symbol, String}, description::Any, execute::Function)
```

# 例

```julia
ReplCmd(:echo, "引数を印刷する", identity)
ReplCmd(:addone, "入力に1を加えたものを返す", v -> 1 + parse(Int, v))
ReplCmd(:math, "基本的な整数算術のコレクション",
    [ReplCmd(:add, "a + b + ...", nums -> sum(parse.(Int, split(nums))))],
     ReplCmd(:mul, "a * b * ...", nums -> prod(parse.(Int, split(nums)))))
```

# メソッド

```julia
help(::ReplCmd) # -> 詳細なヘルプを印刷
allcompletions(::ReplCmd) # -> すべての候補をリスト
completions(::ReplCmd, sofar::AbstractString) # -> 関連する候補をリスト
```
