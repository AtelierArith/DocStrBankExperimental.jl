```
prompt(question::AbstractString, default::AbstractString="",
       allowempty::Bool=false, cleardefault::Bool=true,
       multiline::Bool=false)
```

インタラクティブに `question` を尋ね、応答文字列を返します。オプションで `default` 値を指定できます。`multiline` が true の場合、値を送信するには `RET` を連続して2回押す必要があります。

`allowempty` が設定されていない限り、空の応答は受け付けられません。`cleardefault` が設定されている場合、最初のバックスペースでデフォルト値がクリアされます。

プロンプトは以下の行編集キーをサポートしています：

  * 左矢印
  * 右矢印
  * ホーム
  * エンド
  * 前方削除
  * 後方削除

### 例

```julia-repl
julia> prompt("What colour is the sky? ")
What colour is the sky? Blue
"Blue"
```
