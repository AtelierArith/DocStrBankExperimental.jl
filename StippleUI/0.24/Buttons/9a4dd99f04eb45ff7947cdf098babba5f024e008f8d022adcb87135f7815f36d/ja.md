Stippleには、いくつかの追加機能を備えたボタンである`btn`というコンポーネントがあります。たとえば、デフォルトの長方形と丸の2つの形状があります。また、マテリアルリップル効果が組み込まれており（無効にすることも可能です）、ボタンコンポーネントにはスピナーやローディング効果も付属しています。これは、アプリの実行に遅延が生じる可能性がある場合に、ユーザーにその遅延についてフィードバックを提供するために使用します。使用すると、ユーザーがボタンをクリックした瞬間にスピニングアニメーションが表示されます。

無効化されていない場合やスピニング中でない場合、`btn`はクリックまたはタップされるとすぐに`@click`イベントを発生させます。

### 例

```
julia> btn("Move Left", color = "primary", icon = "mail", @click("press_btn = true"))

julia> btn("Go to Hello World", color = "red", type = "a", href = "hello", icon = "map", iconright = "send")

julia> btn("Connect to server!", color="green", textcolor="black", @click("btnConnect=!btnConnect"), [
          tooltip(contentclass="bg-indigo", contentstyle="font-size: 16px", 
          style="offset: 10px 10px",  "Ports bounded to sockets!")]
       )       
```

---

### 引数

---

1. 動作

      * `loading::Bool` - ボタンをローディング状態にする（`spinner`を表示 – 'loading'スロットを使用することで上書き可能）
      * `percentage::Union{Int, Float64}` - パーセンテージ（0.0 < x < 100.0）；'loading'プロパティと一緒に使用；背景にプログレスバーを表示 ex. `23`
      * `darkpercentage::Bool` - 背景のプログレスバーはダークカラーであるべき；'percentage'および'loading'プロパティと一緒に使用
2. コンテンツ

      * `label::Union{String, Symbol, Nothing}` - ボタンに表示されるテキスト ex. `Button Label`
      * `icon::String` - Quasarの規約に従ったアイコン名；'img:'プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください；'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の不動産は依然として使用されます） ex. `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `iconright::String` - Quasarの規約に従ったアイコン名；'img:'プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください；'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の不動産は依然として使用されます） ex. `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `nocaps::Bool` - ラベルテキストを大文字に変換しない（デフォルトでは大文字になります）
      * `nowrap::Bool` - ラベルテキストの折り返しを避ける
      * `align::String` - ラベルまたはコンテンツのデフォルトの配置。`center`が受け入れられる値。`left` `right` `center` `around` `between` `evenly`
      * `stack::Bool` - アイコンとラベルを同じ行ではなく垂直にスタックする（デフォルトでは同じ行に配置されます）
      * `stretch::Bool` - フレックスボックスの親で使用されると、ボタンは親の高さに合わせて伸びます
3. 一般

      * `type::String` - 1) ボタンのネイティブタイプ属性を定義する（submit、reset、button）または 2) <a>タグでコンポーネントをレンダリングして、無効にしてもイベントにアクセスできるようにするか 3) 'href'プロパティを使用し、'type'をメディアタグのデフォルトとして指定します。 `button` ex. `a` `submit` `reset` `button` `image/png` `href="https://some-site.net" target="_blank"`
      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値
4. ナビゲーション

      * `href::String` - ネイティブ<a>リンクのhref属性；'to'および'replace'プロパティよりも優先されます ex. `https://quasar.dev` `href="https://quasar.dev" target="_blank"`
      * `target::String` - ネイティブ<a>リンクのtarget属性；'to'または'href'プロパティと一緒にのみ使用します ex. `_blank` `_self` `_parent` `_top`
5. 状態

      * `loading::Bool` - ボタンをローディング状態にする（`spinner`を表示 – 'loading'スロットを使用することで上書き可能）
      * `disable::Bool` - コンポーネントを無効モードにする
6. スタイル

      * `size::String` - CSS単位でのサイズ、単位名または標準サイズ名（xs|sm|md|lg|xl）を含む ex. `16px` `2rem` `xs` `md`
      * `ripple::Union{Bool, Dict}` - マテリアルリップルを構成する（'false'に設定することで無効にするか、構成オブジェクトを供給）デフォルト。 `true` ex. `false` `{ "early" => true, "center" => true, "color" => "teal", "keyCodes" => [] }`
      * `outline::Bool` - `outline`デザインを使用
      * `flat::Bool` - `flat`デザインを使用
      * `unelevated::Bool` - シャドウを削除
      * `rounded::Bool` - 四角い形のボタンに対してより顕著なボーダー半径を適用
      * `push::Bool` - 'push'デザインを使用
      * `glossy::Bool` - 光沢効果を適用
      * `fab::Bool` - ボタンのサイズと形状を浮動アクションボタンに合わせる
      * `fabmini::Bool` - ボタンのサイズと形状を小さな浮動アクションボタンに合わせる
      * `padding::String` - カスタムパディングを適用（垂直 [水平]）；CSS単位でのサイズ、単位名または標準サイズ名（none|xs|sm|md|lg|xl）；設定すると最小幅と高さも削除されます
      * `color::String` - コンポーネントの色名 [カラーパレット](https://quasar.dev/style/color-palette) から eg. `primary` `teal-10`
      * `textcolor::String` - テキストカラーを上書き（必要に応じて）；[カラーパレット](https://quasar.dev/style/color-palette) からの色名 eg. `primary` `teal-10`
      * `dense::Bool` - 密なモード；占有スペースが少なくなる
      * `round::Bool` - 円形のボタンを作成
