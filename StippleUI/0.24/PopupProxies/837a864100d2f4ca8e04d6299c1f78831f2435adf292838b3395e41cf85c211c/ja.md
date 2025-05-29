```
  popup_proxy(fieldname::Union{Symbol,Nothing} = nothing, args...; content::Union{String,Vector,Function} = "", kwargs...)
```

`popupproxy`は、より大きな画面では`menu`を、より小さな画面では`dialog`を表示する必要があるときに使用されます。これは、どちらのコンポーネントを使用するかを選択するプロキシとして機能します。`popupproxy`はコンテキストメニューも処理します。

---

### 例

---

### 表示

```julia-repl
julia> btn("クリックを処理", push=true, color="primary", [
          popupproxy([
            banner("インターネットへの接続が失われました。このアプリはオフラインです。", [
              template("", "v-slot:avatar", [
                icon("signal_wifi_off", color="Primary")
              ])
            ])
          ])
       ])
```

---

### 引数

---

1. 動作

      * `target::Union{Bool, String}` - コンポーネントのトグルをトリガーするターゲット要素を設定します。'true'は親DOM要素を有効にし、'false'はDOM要素へのイベントの添付を無効にします。文字列（CSSセレクタ）またはDOM要素を使用すると、指定されたDOM要素（存在する場合）にイベントが添付されます。例：`true`、`target!=false`、`target!=".my-parent"`
      * `noparentevent::Bool` - ターゲットDOM要素（要素を表示するトリガー）へのイベントの添付をスキップします。
      * `contextmenu::Bool` - コンポーネントがコンテキストメニューのように動作することを許可します。これは右クリック（またはモバイルでの長押し）で開きます。
      * `breakpoint::Union{Int, String}` - メニューがダイアログの代わりに使用されるウィンドウの幅/高さ（どちらか小さい方）のブレークポイント（ピクセル単位）。例：`992`、`breakpoint!="1234"`
