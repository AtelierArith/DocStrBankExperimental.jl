```
parameters(S; <キーワード引数>) -> Config
```

システム `S` に対して定義されたパラメータのリストを抽出します。

# 引数

  * `S::Type{<:System}`: 検査するシステムの型。

# キーワード引数

  * `alias=false`: パラメータ名の代わりにエイリアスを表示します。
  * `recursive=false`: `S` に宣言された他のシステムからパラメータを抽出します。
  * `exclude=()`: 再帰的検索で除外されるシステム。
  * `scope=nothing`: 評価スコープ; デフォルトは `S.name.module` です。

# 例

```julia-repl
julia> @system S(Controller) begin
           a: aaa => 1 ~ preserve(parameter)
       end;

julia> parameters(S)
Config for 1 system:
  S
    a = 1

julia> parameters(S; alias=true)
Config for 1 system:
  S
    aaa = 1

julia> parameters(S; recursive=true)
Config for 3 systems:
  Clock
    init = 0 hr
    step = 1 hr
  Context
  S
    a = 1

julia> parameters(S; recursive=true, exclude=(Context,))
Config for 1 system:
  S
    a = 1
```
