```
select(fieldname::Symbol, args...; options::Union{Symbol, Vector}, kwargs...)
```

---

### 例

---

### モデル

```julia-repl
julia> @vars SelectModel begin
          model::R{Vector{String}} = []
          networks::R{Vector{String}} = ["Google", "Facebook", "Twitter", "Pinterest", "Reddit"]
       end
```

### ビュー

```julia-repl
julia> select(:model, options= :networks, useinput=true, multiple=true, clearable = true, filled = true, counter = true, usechips = true, label="ソーシャルネットワーク")
```

---

### 引数

---

1. 挙動

      * `name::String` - コントロールの名前を指定するために使用されます; フォームを扱う場合に便利です; 指定されていない場合は、存在する場合は 'for' プロパティの値を取ります ex. `car-id` `car-id`
      * `virtualscrollhorizontal::Bool` - バーチャルリストを横モードで動作させます
      * `error::Bool` - フィールドに検証エラーがありますか？
      * `rules::Vector` - 関数/文字列の配列; 文字列の場合は、埋め込まれた検証ルールの1つの名前でなければなりません `rules="[ val => val.length <= 3 || '最大3文字を使用してください' ]"`
      * `reactiverules::Bool` - デフォルトでは、ルールの変更はモデルが変更されるまで新しい検証をトリガーしません; trueに設定すると、ルールの変更が検証をトリガーします; パフォーマンスにペナルティがあるため、本当に必要な場合のみ使用してください
      * `lazyrules::Union{Bool, String}` - ブール値trueに設定すると、フィールドが最初にフォーカスを失った後にのみ 'rules' に対して検証ステータスをチェックします; 'ondemand' に設定すると、コンポーネントの validate() メソッドが手動で呼び出されたとき、またはラッパー `form` が自分自身を送信するときにのみトリガーされます ex. `(Boolean) true` `(Boolean) false` `ondemand`
      * `loading::Bool` - スピナーを表示することで、プロセスが進行中であることをユーザーに通知します; スピナーは 'loading' スロットを使用してカスタマイズできます。
      * `clearable::Bool` - 値（未定義またはnullでない）が設定されているときにクリア可能なアイコンを追加します; クリックすると、モデルはnullになります
      * `autofocus::Bool` - 初期コンポーネントレンダリング時にフィールドにフォーカスを当てます
      * `for::String` - コントロールの 'id' を指定するために使用され、ラベルをラップする 'for' 属性も指定します; 'name' プロパティが指定されていない場合、この属性にも使用されます `myFieldsId`
      * `hidedropdownicon::Bool` - ドロップダウンアイコンを非表示にします
      * `fillinput::Bool` - 現在の値で入力を埋めます; 'hideselected' と一緒に使用すると便利です; 'multiple' 選択と一緒には機能しません
      * `newvaluemode::String` - 新しい値の作成を有効にし、新しい値が追加されたときの動作を定義します: 'add' は値を追加します（重複の可能性があっても）、'add-unique' はユニークな値のみを追加し、'toggle' は値を追加または削除します（存在するかどうかに基づいて）; このプロパティを使用する場合、`newvalue` をリスニングすることはオプションになります（`newvaluemode` によって定義された動作をオーバーライドするためのみ） ex. `add` `add-unique` `toggle`
      * `autocomplete::String` - フィールドのオートコンプリート属性 ex. `autocomplete="country"`
      * `transitionshow::String` - メニュー/ダイアログを表示するときのトランジション; [埋め込まれたトランジション](https://v1.quasar.dev/options/transitions) の1つ ex. `fade` `slide-down`
      * `transitionhide::String` - メニュー/ダイアログを隠すときのトランジション; [埋め込まれたトランジション](https://v1.quasar.dev/options/transitions) の1つ ex. `fade` `slide-down`
      * `behavior::String` - デスクトップではメニューとして、モバイルではダイアログとして表示するデフォルトの動的モードをオーバーライドします `default` `menu` `dialog`
2. コンテンツ

      * `tablecolspan::Union{Int, String}` - テーブルの列数（table-layout: fixed を使用する場合に必要です） ex. `tablecolspan="12"`
      * `errormessage::String` - 検証エラーメッセージ（'error' が 'true' に設定されている場合のみ表示されます） ex. `ユーザー名は少なくとも5文字でなければなりません`
      * `noerroricon::Bool` - エラーがある場合にエラーアイコンを非表示にします
      * `label::Union{String,Symbol,Nothing}` - フィールドがフォーカスを得ると、入力フィールドの上に「浮かぶ」テキストラベル ex. `ユーザー名`
      * `stacklabel::Bool` - フィールドの内容に関係なく、ラベルが常にフィールドの上に表示されます（あれば）
      * `hint::String` - ラップされたフォームコンポーネントの下に配置されるヘルパー（ヒント）テキスト ex. `3文字から12文字の間で入力してください`
      * `hidehint::Bool` - フィールドがフォーカスを持っていないときにヘルパー（ヒント）テキストを非表示にします
      * `prefix::String` - プレフィックス ex. `$`
      * `suffix::String` - サフィックス ex. `@gmail.com`
      * `loading::Bool` - スピナーを表示することで、プロセスが進行中であることをユーザーに通知します; スピナーは 'loading' スロットを使用してカスタマイズできます。
      * `clearable::Bool` - 値（未定義またはnullでない）が設定されているときにクリア可能なアイコンを追加します; クリックすると、モデルはnullになります
      * `clearicon::String` - 'clearable' 属性と一緒に使用するクリアボタンのカスタムアイコン ex. `close`
      * `labelslot::Bool` - ラベルスロットを有効にします; 'label' プロパティが設定されていない場合、'label' スロットの使用を強制するために設定する必要があります
      * `bottomslots::Bool` - ボトムスロット（'error', 'hint', 'counter'）を有効にします
      * `counter::Bool` - 右下に自動カウンターを表示します
      * `dropdownicon::String` - アイコン名; アイコンライブラリがインストールされていることを確認してください; 'img:' プレフィックスを使用していない限り; 'none'（文字列）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます） ex. `map` `ion-add` `img=https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img=path/to/some_image.png`
      * `useinput::Bool` - ユーザーが入力できる入力タグを使用します
      * `inputdebounce::Union{Int, String}` - 入力モデルの更新をミリ秒単位でデバウンスします ex. `500` `600`
3. 一般

      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値 ex. `0` `100`
4. モデル

      * `multiple::Bool` - 複数選択を許可します; モデルは配列でなければなりません
      * `emitvalue::Bool` - 選択されたオプションの値でモデルを更新します（オプション全体ではなく）
5. オプション

      * `options::Vector` - ユーザーが選択できる利用可能なオプション。パフォーマンスを最適化するためにオプションのリストをフリーズします ex. `options = [ "BMW", "Samsung Phone" ]`
      * `optionvalue::String` - 'value' を保持するオプションのプロパティ; 関数を使用する場合は、パフォーマンスを最適化するためにスコープから参照し、インラインで定義しないでください ex. `optionvalue=modelNumber` `optionvalue="(item) => item === null ? null : item.modelNumber"`
      * `optionlabel::Union{String,Symbol}` - 'label' を保持するオプションのプロパティ; 関数を使用する場合は、パフォーマンスを最適化するためにスコープから参照し、インラインで定義しないでください ex. `optionlabel=itemName` `optionlabel="(item) => item === null ? null : item.itemName"`
      * `optiondisable::String` - 無効であることを示すオプションのプロパティ; プロパティの値はブール値でなければなりません; 関数を使用する場合は、パフォーマンスを最適化するためにスコープから参照し、インラインで定義しないでください ex. `optiondisable=cannotSelect` `optiondisable="(item) => item === null ? null : item.cannotSelect"`
      * `optionsdense::Bool` - オプションリストの密なモード; より少ないスペースを占有します
      * `optionsdark::Bool` - オプションメニューが暗い色で着色されます
      * `optionsselectedclass::String` - アクティブ/選択されたオプションのCSSクラス名; デフォルトの適用を停止するには空の文字列に設定します（デフォルトは text-* で、* は 'color' プロパティの値です） ex. `text-orange`
      * `optionssanitize::Bool` - オプションを描画するために textContent の使用を強制します; オプションが安全でない可能性がある場合（ユーザー入力から）に使用します; 'option' スロットを使用している場合は適用されません!
      * `optionscover::Bool` - 拡張メニューがコンポーネントを覆います（明らかな理由から `useinput` 属性と一緒には機能しません）
      * `menushrink::Bool` - オプションリストがフィールドよりも狭くなることを許可します（メニューモードのみ）
      * `mapoptions::Bool` - `options` ベクターからモデルのラベルをマッピングしようとします; 小さなパフォーマンスペナルティがあります; emit-value を使用している場合、選択フィールドに値ではなくラベルテキストを表示するために map-options を使用する必要があります; 上記の 'モデルに影響を与える' セクションを参照してください
6. 位置

      * `menuanchor::String` - フィールドに対するオプションリストの開始位置またはアンカーポイントを設定する2つの値（メニューモードのみ） ex. `top left` `top middle` `top right` `top start` `top end` `center left` `center middle` `center right` `center start` `center end` `bottom left` `bottom middle` `bottom right` `bottom start` `bottom end`
      * `menuself::String` - ターゲットに対するオプションリストの自身の位置を設定する2つの値（メニューモードのみ） ex. `top left` など
      * `menuoffset::Vector` - オプションリストを水平方向および垂直方向にピクセル単位でオフセットするための2つの数値の配列（メニューモードのみ） ex. `[8, 8]`
7. 選択

      * `multiple::Bool` - 複数選択を許可します; モデルは配列でなければなりません
      * `displayvalue::Union{Int, String}` - デフォルトの選択文字列をオーバーライドします; `selected` スロット/スコープスロットを使用していない場合、または `usechips` 属性を使用していない場合
      * `displayvaluesanitize::Bool` - 選択されたオプションを描画するために textContent の使用を強制します; 選択されたオプションが安全でない可能性がある場合（ユーザー入力から）に使用します; `selected` または `selecteditem` スロットを使用している場合は適用されません!
      * `hideselected::Bool` - 選択を隠します; 選択されたオプションのラベルを表示するために基礎となる入力タグを使用します（入力の右側に表示するのではなく）; 非 `multiple` セレクトにのみ機能します
      * `maxvalues::Union{Int, String}` - ユーザーが行うことができる最大選択数を許可します ex. `5`
      * `usechips::Bool` - 現在選択されているものを表示するために `chip` コンポーネントを使用します
8. 状態

      * `disable::Bool` - コンポーネントを無効モードにします
      * `readonly::Bool` - コンポーネントを読み取り専用モードにします
9. スタイル

      * `labelcolor::String` - [カラーパレット](https://quasar.dev/style/color-palette) からラベルの色名; `color` プロパティをオーバーライドします; `color` プロパティとの違いは、フィールドがフォーカスされていないときでもラベルは常にこの色を持つことです ex. `primary` `teal-10`
      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette) からコンポーネントの色名
      * `bgcolor::String` - [カラーパレット](https://quasar.dev/style/color-palette) からコンポーネントの背景色名
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `filled::Bool` - フィールドに `filled` デザインを使用します
      * `outlined::Bool` - フィールドに `outlined` デザインを使用します
      * `borderless::Bool` - フィールドに `borderless` デザインを使用します
      * `standout::Union{Bool, String}` - フィールドに 'standout' デザインを使用します; フォーカス時に適用されるクラスを指定します（デフォルトのものをオーバーライド） ex. `standout` `standout="bg-primary text-white"`
      * `hidebottomspace::Bool` - これらが使用されていないときにヒント/エラー/カウンターのためのスペースをもう予約しません; その結果、これらのアニメーションも無効になります; ヒント/エラーエリアがその内容に基づいて垂直に伸びることも許可します
      * `rounded::Bool` - コンポーネントの角を小さく標準のボーダー半径を適用します
      * `square::Bool` - ボーダー半径を削除してボーダーを四角くします; `rounded` プロパティ/属性をオーバーライドします
      * `dense::Bool` - 密なモード; より少ないスペースを占有します
      * `itemaligned::Bool` - 内部コンテンツの整列を `item` コンポーネントのそれに一致させます
      * `popupcontentclass::String` - ポップアップコンテンツに適用されるクラス定義 ex. `my-special-class`
      * `popupcontentstyle::Union{Vector, String, Dict}` - ポップアップコンテンツに適用されるスタイル定義 ex. `background-color: #ff0000` `popupcontentstyle!="{ backgroundColor: '#ff0000' }"`
      * `inputclass::Union{Vector, String, Dict}` - 基礎となる入力タグに適用されるクラス定義 ex. `my-special-class` `inputclass!="{ 'my-special-class': <condition> }"`
      * `inputstyle::Union{Vector, String, Dict}` - 基礎となる入力タグに適用されるスタイル定義 ex. `background-color: #ff0000` `inputstyle!="{ backgroundColor: '#ff0000' }"`
10. バーチャルスクロール

      * `virtualscrollslicesize::Union{Int, String}` - バーチャルリストにレンダリングする最小アイテム数 ex. `virtualscrollslicesize="60"` `30`
      * `virtualscrollsliceratiobefore::Union{Int, String}` - 表示ゾーン内のアイテム数の比率をレンダリングする前 ex. `virtualscrollsliceratiobefore="30"` `30`
      * `virtualscrollsliceratioafter::Union{Int, String}` - 表示ゾーン内のアイテム数の比率をレンダリングする後 ex. `virtualscrollsliceratioafter="0.3"`
      * `virtualscrollitemsize::Union{Int, String}` - アイテムのデフォルトサイズ（垂直の場合は高さ、横の場合は幅）; この値は初期リストのレンダリングに使用されます; アイテムの最小サイズに近い値を使用するようにしてください ex. `virtualscrollitemsize="48"`
      * `virtualscrollstickysizestart::Union{Int, String}` - リストの開始時に使用するスティッキーパートのサイズ（垂直の場合は高さ、横の場合は幅）; 正しい値はスクロール精度を向上させます ex. `0` `virtualscrollstickysizestart="23`
      * `virtualscrollstickysizeend::Union{Int, String}` - リストの終了時に使用するスティッキーパートのサイズ（垂直の場合は高さ、横の場合は幅）; 正しい値はスクロール精度を向上させます ex. `0`
      * `tablecolspan::Union{Int, String}` - テーブルの列数（table-layout: fixed を使用する場合に必要です） ex. `tablecolspan="3"`
