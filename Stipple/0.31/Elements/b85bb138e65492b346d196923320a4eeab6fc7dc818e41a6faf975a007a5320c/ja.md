```
on(action, expr)
```

指定された Vue コンポーネントの `action` によって呼び出される js ルーチンを定義します。例: `:click`, `:input`

### 例

```julia
julia> input("", @bind(:input), @on("keyup.enter", "process = true"))
"<input  v-model='input' v-on:keyup.enter='process = true' />"
```

`expr` がシンボルの場合、イベントはバックエンドに送信されます。イベントを処理するためには、対応する `Stipple.notify` メソッドを手動で定義するか、`@event` マクロを使用する必要があります。

### 例

```julia
julia> Stipple.notify(model, ::Val{:my_click}) = println("clicked")
```

または、イベント情報が必要な場合

```julia
Stipple.notify(model, ::Val{:my_click}, event_info) = println(event_info)
```

または `@event` マクロを使用して：

```julia
@event :my_click begin
  @info "clicked, event_info is " event
  notify(__model__, "Info from the backend: Clicked")
end
```

ハンドラー内で `model` は受信モデルを指し、event はイベント情報の Dict です。ハンドラーは UI 要素にリンクされています。

```julia
btn("Event test", @on("click", :my_click))
```

時にはイベントの前処理が必要です。例えば、情報を追加したりスキップしたりするためです。

```julia
@on(:uploaded, :uploaded, "for (f in event.files) { event.files[f].fname = event.files[f].name }")
```

これは、クリックイベントの場合など、すべてのフィールドが JSON.stringify によって自動的に変換されるわけではないため必要です。他のイベント、例えば `q-table` コンポーネントの `row-clicked` イベントは、イベント自体だけでなく、より多くの引数を渡します。これらの引数は `args` としてアクセス可能です。

```julia
table(:table, @on(:row__click, :rowclick, "event.row = args[0]"))
```

事前定義されたハンドラーを前処理器として使用することもできます。これは、複数のイベントに対して同じハンドラーを使用したい場合に便利です。ハンドラー名はシンボルとして渡されます。

```julia
@methods [
    :addTableIndex => js"""
        function (event, row, id) {
            const keys = Object.keys(row)
            event.row = id + 1;
            event.column = event.target.closest('td').cellIndex + 1;
            event.value = row[keys[event.column]];
            event.row_data = row;
            event.column_keys = keys;
            return event;
        }
    """
]

cell(@on(:click, :rowclick, :addTableIndex))
```

最後に、ハンドラーの配列を前処理器として渡すこともできます。この場合、各ハンドラーがイベントオブジェクトを返すことを確認してください。ハンドラーはチェーンされます。シンボルと文字列の混合も可能です。

```julia
cell(@click("rowclick", [:addTableIndex, "console.log('Click coords: ' + event.clientX + '|' + event.clientY)", :myHandler]))
```
