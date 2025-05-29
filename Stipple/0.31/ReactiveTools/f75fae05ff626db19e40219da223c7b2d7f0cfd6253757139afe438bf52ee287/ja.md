```julia
@event(event, expr)
```

特定の `event` が UI コンポーネントによってトリガーされたときに、`expr` 内のコードを実行します。

**使用法**

@on マクロを使用して、コンポーネントのクリック、キー入力、またはファイルアップロードなどのイベントトリガーを定義します。次に、@event でイベントのハンドラーを定義します。

**例**

キー入力:

```julia
@app begin
  @in n = 1
end

@event :keypress begin
    println("Enter キーが押されました")
end

ui() =  textfield(class = "q-my-md", "Input", :input, hint = "いくつかの単語を入力してください", @on("keyup.enter", :keypress))

@page("/", ui)
```

html 出力

```html
<q-input hint="いくつかの単語を入力してください" v-on:keyup.enter="function(event) { handle_event(event, 'keypress') }" label="Input" v-model="input" class="q-my-md"></q-input>
```

ファイルアップロード:

```julia
@app begin
  @in n = 1
end

@event :uploaded begin
    println("ファイルがアップロードされました！")
end

ui() = uploader("ファイルをアップロード", url = "/upload" , method="POST", @on(:uploaded, :uploaded), autoupload=true)

route("/upload", method=POST) do
    # アップロードされたファイルを処理する
end

@page("/", ui)
```

html 出力

```html
<q-uploader url="/upload" method="POST" auto-upload v-on:uploaded="function(event) { handle_event(event, 'uploaded') }">ファイルをアップロード</q-uploader>
```

ファイナライザー:

```julia
@event :finalize begin
    @info "特別なファイナライザーを呼び出しています"
    # クリーンアップを行う
    # ...
    # その後、デフォルトのファイナライザーを呼び出す
    notify(__model__, Val(:finalize))
end
```
