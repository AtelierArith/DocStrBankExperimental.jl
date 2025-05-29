```
parameters(s; <キーワード引数>) -> Config
```

既存のシステム `s` のインスタンスからパラメータのリストを抽出します。

# 引数

  * `s::System`: 検査されるシステムのインスタンス。

# キーワード引数

  * `alias=false`: パラメータ名の代わりにエイリアスを表示します。
  * `recursive=false`: `S` に宣言された他のシステムからパラメータを抽出します。
  * `exclude=()`: 再帰的検索で除外されるシステム。

# 例

```julia-repl
julia> @system S(Controller) begin
           a: aaa => 1 ~ preserve(parameter)
       end;

julia> s = instance(S; config = :S => :a => 2);

julia> parameters(s)
Config for 1 system:
  S
    a = 2.0

julia> parameters(s; alias = true)
Config for 1 system:
  S
    aaa = 2.0

julia> parameters(s; recursive = true)
Config for 3 systems:
  Clock
    init = 0.0 hr
    step = 1.0 hr
  Context
  S
    a = 2.0

julia> parameters(s; recursive = true, exclude = (Context,))
Config for 1 system:
  S
    a = 2.0
```
