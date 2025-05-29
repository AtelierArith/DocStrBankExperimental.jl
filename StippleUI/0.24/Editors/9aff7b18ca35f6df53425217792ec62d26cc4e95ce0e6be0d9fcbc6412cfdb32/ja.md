editor(fieldname, args...; kwargs...)

コンポーネントはWYSIWYG（「見たまま編集」）エディタコンポーネントで、ユーザーがHTMLを記述したり、貼り付けたりすることを可能にします。

---

### 例

---

### モデル

```julia-repl
julia> @vars EditorModel begin
          s_editor::R{String} = "What you see is <b>what</b> you get."
       end
```

### ビュー

```julia-repl
julia> editor(:s_editor, minheight="5rem")

julia> StippleUI.form( autocorrect="off", autocapitalize="off", autocomplete="off", spellcheck="false", [
          editor(:s_editor)
       ])
```

---

### 引数

---

]

1. 挙動

      * `fullscreen::Bool` - フルスクリーンモード。例: `fullscreen = :isFullscreen`
      * `noroutefullscreenexit::Bool` - ルートアプリの変更がフルスクリーンを終了させない
      * `paragraphtag::String` - 使用する段落タグ。例: `div`, `p`
2. コンテンツ

      * `placeholder::String` - プレースホルダーとして表示するテキスト。例: `Type your story here...`
3. モデル

      * `value::String` [必須!] - コンポーネントのリアクティブモデル
4. 状態

      * `readonly::Bool` - コンポーネントを読み取り専用モードにする
      * `disable::Bool` - コンポーネントを無効にする
5. スタイル     

      * `square::Bool` - ボーダー半径を削除し、ボーダーを四角くする
      * `minheight::String` - コンポーネントの最小高さ。デフォルト: `10rem` 例: `15rem` `50vh`
      * `flat::Bool` - 'フラット'デザイン（ボーダーなし）を適用
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知
      * `maxheight::String` - 入力エリアの最大高さのCSS単位。例: `100px` `90vh`
      * `height::String` - 編集可能エリアの高さを設定するCSS値。例: `100px` `90vh`
      * `toolbaroutline::Bool` - ツールバーのボタンが「アウトライン」表示される
      * `toolbarpush::Bool` - ツールバーのボタンが「プッシュボタン」タイプとして表示される
      * `toolbarrounded::Bool` - ツールバーのボタンが「丸みを帯びた」表示される
      * `contentstyle::Dict` - `editor`のコンテナのスタイリングのためのCSSプロパティと値を持つオブジェクト。例: `contentstyle!="{ backgroundColor: '#C0C0C0' }"`
      * `contentclass::Union{Dict, Vector, String}` - 入力エリアのCSSクラス。例: `my-special-class` `contentclass!="{ 'my-special-class': <condition> }"`
