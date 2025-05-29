```
ShowLimit
```

オブジェクトを表示するための `AbstractShow` ラッパーで、表示される文字列の長さを固定の文字数に制限します。

## コンストラクタ

  * `ShowLimit(o; limit=typemax(Int), n=0, continuation_string="…", check_brackets=true)`

## 引数

  * `o`: ラップするオブジェクト。
  * `limit`: 開始デリミタと継続文字列を除いた最大文字数。
  * `n::Integer`: 表示される文字列の開始位置。これは、固定の制限で複数の出力を表示する場合に便利です。例えば、`n=1` で `limit=3` は `limit=2` と同等です。
  * `continuation_string::AbstractString`: 制限に達した場合に印刷される文字列。制限にはカウントされません。
  * `check_brackets`: 表示される文字列の先頭に開き括弧が存在するかどうかを確認するかどうか。これは、制限に達しているかどうかに関係なく閉じ括弧を表示するのに便利です。

## 例

```
julia> ShowLimit(123, limit=2)
12…

julia> ShowLimit("abc", limit=2)
"a…"

julia> ShowLimit("abc", limit=2, check_brackets=false)
"a…

julia> ShowLimit(123, limit=2, n=1)
1…
```
