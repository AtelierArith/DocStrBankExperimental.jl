```
ShowEntry
```

リスト内のエントリを表示するための `AbstractShow` ラッパータイプ。リストコンテキストオプションの指定を可能にします。

## コンストラクタ

  * `ShowEntry(o; new_line=false, indent="    ", delim=Print(", "))`

## 引数

  * `o`: ラップするオブジェクト。
  * `new_line::Bool`: エントリを新しい行に表示（または印刷）するかどうか。
  * `indent::AbstractString`: 新しい行が作成される場合（すなわち `new_line=true` の場合）、作成された行はこのインデントで始まります。
  * `delim`: エントリの最後に表示されるオブジェクト、通常はカンマです。渡されたオブジェクトはそのまま表示されるため、例えば `", "` は引用符を印刷します。引用符を省略するには `Print(", ")` を使用します。

## 例

```
julia> ShowEntry(1)  # デフォルトではカンマが表示されます
1,


julia> ShowEntry("a", new_line=true, indent="__", delim=Print(": "))

__"a":
```
