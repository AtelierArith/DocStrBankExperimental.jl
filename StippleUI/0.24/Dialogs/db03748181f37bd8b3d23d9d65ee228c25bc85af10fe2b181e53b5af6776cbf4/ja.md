```
dialog()
```

`dialog`コンポーネントは、ユーザーに特定のアクションまたはアクションのリストを選択する機会を提供する素晴らしい方法です。また、ユーザーに重要な情報を提供したり、決定（または複数の決定）を下す必要がある場合にも使用できます。

> TIP: ダイアログは、ネイティブJSの`alert()`、`prompt()`などの基本的な使用ケースのために、グローバルに利用可能なメソッドとしても使用できます。


---

### 例

---

### モデル

```julia-repl
julia> @vars DialogModel begin
         show_dialog::R{Bool} = false
       end
```

### ビュー

```julia-repl
julia> Html.div(class="q-pa-md q-gutter-sm", [
        btn("Alert", color="primary", @click("show_dialog = true")),
        StippleUI.dialog(:show_dialog, [
          card([
            card_section(Html.div(class="text-h6", "Alert")),
            card_section(class="q-pt-none", "Lorem ipsum dolor sit amet consectetur adipisicing elit. 
            Rerum repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis perferendis totam, 
            ea at omnis vel numquam exercitationem aut, natus minima, porro labore.")
          ])
        ])
      ])
```

---

### 引数

---

1. 挙動

      * `persistent::Bool` - ユーザーはダイアログの外をクリックしたりESCキーを押したりしてダイアログを閉じることができません。また、アプリのルート変更でもダイアログは閉じません
      * `noesc::Bool` - ユーザーはESCキーを押してダイアログを閉じることができません; 'persistent'プロパティが設定されている場合は設定する必要はありません
      * `nobackdrop::Bool` - ユーザーはダイアログの外をクリックしてダイアログを閉じることができません; 'persistent'プロパティが設定されている場合は設定する必要はありません
      * `autoclose::Bool` - ダイアログ内の任意のクリック/タップでダイアログが閉じます
      * `transitionshow::String` - [埋め込みトランジション](https://v1.quasar.dev/options/transitions)の1つ eg. `"fade"`, `"slide-down"`
      * `transitionhide::String` - [埋め込みトランジション](https://v1.quasar.dev/options/transitions)の1つ eg. `"fade"`, `"slide-down"`
      * `norefocus::Bool` - (アクセシビリティ) ダイアログが隠れたとき、以前にフォーカスがあったDOM要素に再フォーカスしない
      * `nofocus::Bool` - (アクセシビリティ) ダイアログが表示されたとき、フォーカスを切り替えない
2. コンテンツ

      * `seamless::Bool` - ダイアログをシームレスモードにする; バックドロップを使用しないため、ユーザーはページの残りの部分とも対話できます
      * `maximized::Bool` - ダイアログを最大化モードにする
      * `fullwidth::Bool` - ダイアログはウィンドウと同じ幅でレンダリングしようとします
      * `fullheight::Bool` - ダイアログはウィンドウと同じ高さでレンダリングしようとします
      * `position::String` - ダイアログを一方の側に固定する（"top", "right", "bottom"または"left"）
3. スタイル

      * `contentclass::Union{Array, String}` - コンテンツに割り当てるクラス定義 eg. `"my-special-class"` `:content-class="{ 'my-special-class': <condition> }"`
      * `contentstyle::Union{Array, String}` - コンテンツに割り当てるスタイル定義 eg. `"background-color: #ff0000"` `:content-style="{ color: '#ff0000' }"`
      * `square::Bool` - コンテンツに四角い境界を強制します
