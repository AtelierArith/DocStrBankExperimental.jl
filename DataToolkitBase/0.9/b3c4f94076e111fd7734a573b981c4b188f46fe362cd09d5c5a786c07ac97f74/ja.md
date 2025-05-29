Lintアイテムの表現。

# コンストラクタ

```julia
LintItem(source, severity::Union{Int, Symbol}, id::Symbol, message::String,
         fixer::Union{Function, Nothing}=nothing, autoapply::Bool=false)
```

`source`は、リントが適用されるオブジェクトです。

`severity`は次のいずれかの値である必要があります：

  * `0`または`:debug`、特定の構成に関連する問題のデバッグを支援する可能性のあるメッセージ。
  * `1`または`:info`、エンドユーザーが理解できる情報メッセージ。
  * `2`または`:warning`、潜在的に有害な状況。
  * `3`または`:error`、通常の機能を妨げる重大な問題。

`id`はリントのタイプを表すシンボルです（例：`:unknown_driver`）

`message`は、`source`に関する問題の特定の性質を説明する、エンドユーザーに理解可能なメッセージです。できるだけ具体的であるべきです。

`fixer`は、問題を解決するために`source`を修正する関数に設定できます。`autoapply`が`true`に設定されている場合、`fixer`は自発的に呼び出されます。この関数は、問題を正常に修正できたかどうかを示すために`true`または`false`を返す必要があります。

一般的なルールとして、ユーザー入力を必要とする可能性のあるフィクサーは自動的に実行されるべきではなく、ユーザー入力なしで実行でき、常に「正しいことをする」フィクサーは自動的に実行されるべきです。

# 例

TODO

# 構造

```julia
struct LintItem{S}
    source    ::S
    severity  ::UInt8
    id        ::Symbol
    message   ::String
    fixer     ::Union{Function, Nothing}
    autoapply ::Bool
end
```
