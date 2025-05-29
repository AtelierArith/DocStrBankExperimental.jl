`btndropdown`は非常に便利なドロップダウンボタンです。ドロップダウンコンテンツとして`list`と非常に相性が良いですが、それに限らず使用できます。

ボタンの代わりにドロップダウン「入力」を探している場合は、代わりにSelectを使用してください。

### 例

```
julia> btndropdown(label = "Dropdown Button", color = "primary", [
            list([
              item("Spain", clickable = true, vclosepopup = true, @click("first_item = true")),
              item("USA", clickable = true, vclosepopup = true, @click("second_item = true")),
              item("Netherlands", clickable = true, vclosepopup = true, @click("third_item = true"))
            ]),
       ])
```

---

### 引数

---

1. 動作

      * `loading::Bool` - ボタンをローディング状態にする（`spinner`を表示 – 'loading'スロットを使用することで上書き可能）
      * `split::Bool` - ドロップダウンアイコンを独自のボタンに分割
      * `disablemainbtn::Bool` - メインボタンを無効にする（'split'プロパティと一緒に使用するのに便利）
      * `disabledropdown::Bool` - ドロップダウンを無効にする（'split'プロパティを使用している場合はドロップダウンボタン）
      * `persistent::Bool` - メニューをメニュー外のクリック/タップやESCキーで閉じないようにする
      * `autoclose::Bool` - メニュー内の任意のクリック/タップでメニューを閉じることを許可する; メニューアイテムごとにクリック/タップでメニューを閉じるイベントを添付する代わりに便利
2. コンテンツ

      * `label::Union{String, Int}` - ボタンに表示されるテキスト ex. `"Button Label"`
      * `icon::String` - Quasarの規約に従ったアイコン名; 'img:'プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます） ex. `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `iconright::String` - Quasarの規約に従ったアイコン名; 'img:'プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます） ex. `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `nocaps::Bool` - ラベルテキストを大文字に変換しない（デフォルトでは大文字になります）
      * `nowrap::Bool` - ラベルテキストの折り返しを避ける
      * `align::String`  - ラベルまたはコンテンツのデフォルトの配置。 `center` ex. `"left"` `"right"` `"center"` `"around"` `"between"` `"evenly"`
      * `stack::Bool` - アイコンとラベルを同じ行ではなく垂直にスタックする（デフォルトでは同じ行に配置されます）
      * `stretch::Bool` - フレックスボックスの親で使用されると、ボタンは親の高さに合わせて伸びます
      * `split::Bool` - ドロップダウンアイコンを独自のボタンに分割
      * `dropdownicon::String` - Quasarの規約に従ったアイコン名; 'img:'プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます） ex. `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
3. 一般

      * `type::String` - 1) ボタンのネイティブタイプ属性を定義（submit、reset、button）または 2) <a>タグでコンポーネントをレンダリングして、無効にしてもイベントにアクセスできるようにするか、3) 'href'プロパティを使用して、デフォルトのメディアタグとして'type'を指定します。 `"button"` ex. `"a"` `"submit"` `"reset"` `"button"` `"image/png"` `href="https://some-site.net" target="_blank"`
      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値 ex. `0` `100`
4. ナビゲーション

      * `href::String` - ネイティブ<a>リンクのhref属性; 'to'および'replace'プロパティよりも優先されます ex. `"https://quasar.dev"` `href="https://quasar.dev" target="_blank"`
      * `target::String` - ネイティブ<a>リンクのtarget属性; 'to'または'href'プロパティと一緒にのみ使用します ex. `"_blank"` `"_self"` `"_parent"` `"_top"`
5. 位置

      * `cover::Bool` - メニューがボタンを覆うことを許可します。使用すると、'menu-self'および'menu-fit'プロパティはもはや効果がありません
      * `menuanchor::String` - メニューの開始位置またはターゲットに対するアンカーポイントを設定する2つの値のデフォルト。 `"bottom end"` ex. `"top start"` `"bottom start"` `"top end"` `"bottom end"` `"right start"` `"right end"` `"left start"` `"left end"`
      * `menuself::String` - メニューのターゲットに対する自身の位置を設定する2つの値のデフォルト。 `"top end"` ex. `"top start"` `"bottom start"` `"top end"` `"bottom end"` `"right start"` `"right end"` `"left start"` `"left end"`
      * `menuoffset::Vector` - メニューを水平方向および垂直方向にオフセットするための2つの数値の配列 ex. `[8,8]` `[5,10]`
6. 状態

      * `loading::Bool` - ボタンをローディング状態にする（`spinner`を表示 – 'loading'スロットを使用することで上書き可能）
      * `disable::Bool` - コンポーネントを無効状態にする
7. スタイル

      * `size::String` - CSS単位またはパーセンテージでのサイズ、 ex. `"25px"` `"2.5em"` `"md"` `"xs"`
      * `ripple::Union{Bool, Dict}` - マテリアルリップルを設定（'false'に設定することで無効にするか、設定オブジェクトを供給）デフォルト。 `true` ex. `false` `{ "early" => true, "center" => true, "color" => "teal", "keyCodes" => []}`
      * `outline::Bool` - 'outline'デザインを使用
      * `flat::Bool` - 'flat'デザインを使用
      * `unelevated::Bool` - シャドウを削除
      * `rounded::Bool` - 四角い形のボタンに対してより目立つボーダー半径を適用
      * `push::Bool` - 'push'デザインを使用
      * `glossy::Bool` - 光沢効果を適用
      * `fab::Bool` - ボタンのサイズと形状を浮動アクションボタンに合わせる
      * `fabmini::Bool` - ボタンのサイズと形状を浮動アクションボタンミニに合わせる
      * `padding::String` - カスタムパディングを適用（垂直 [水平]）； CSS単位でのサイズ、単位名または標準サイズ名（none|xs|sm|md|lg|xl）を含む; 設定すると最小幅と高さも削除されます ex. `"16px"`,`"2rem"` ,`"xs"` ,`"md lg"` ,`"2px 2px 5px 7px"`
      * `color::String` - [Quasar Color Palette](https://quasar.dev/options/color-palette)からのコンポーネントの色名 ex. `"primary"` `"teal-10"`
      * `textcolor::String` - テキストカラーを上書き（必要に応じて）； [Quasar Color Palette](https://quasar.dev/options/color-palette)からの色名 ex. `"white"` `"primary"` `"teal-10"`
      * `dense::Bool` - 密なモード; より少ないスペースを占有
      * `noiconanimation::Bool` - 状態が切り替わるときのドロップダウンアイコンの回転を無効にする
      * `contentstyle::Union{Vector, String, Dict}` - メニューに属性を付与するスタイル定義 ex. `{"background-color" => "#ff0000"}` `contentclass!="{ 'my-special-class': <condition> }"`
      * `contentclass::Union{Vector, String, Dict}` - メニューに属性を付与するクラス定義 ex. `"my-special-class"` `contentclass!="{ 'my-special-class': <condition> }"`
