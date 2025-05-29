```
textfield(fieldname, args...; kwargs...)
```

---

### 例

---

### モデル

```julia-repl
julia> @vars TextField begin
          name::R{String} = ""
       end
```

### ビュー

```julia-repl
julia> textfield("あなたの名前は何ですか *", :name, name = "name", @if(:warin), :filled, hint = "名前と姓", "lazy-rules",
          rules = "[val => val && val.length > 0 || '何かを入力してください']"
       )
```

---

### 引数

---

1. 一般     * `type::String` - 次のいずれかでなければなりません: `text (デフォルト)`, `textarea`, `email`, `tel`, `number`, `password` および `url`。これは、モバイルデバイスでポップアップするキーボードのタイプを決定するため重要です。
2. 挙動     * `name::String` - コントロールの名前を指定するために使用されます; フォームを扱う場合に便利です; 指定されていない場合は、存在する場合は 'for' プロパティの値を取ります ex. `car_id`     * `mask::String` - カスタムマスクまたは事前定義されたマスク名のいずれか ex. `date` `datetime` `time` `fulltime` `phone` `card`     * `fillmask::Union{Bool, String}` - 指定された文字（または値が文字列でない場合はアンダースコア）でマスクの長さを埋める ex. `true` `0` `_`     * `reversefillmask::Bool` - マスクの右側から文字列を埋めます     * `unmaskedvalue::Bool` - モデルはマスクされません（トークン/区切り文字を含まない）     * `error::Bool` - フィールドに検証エラーがありますか？     * `rules::Vector` - 関数/文字列の配列; 文字列の場合は、埋め込まれた検証ルールの1つの名前でなければなりません ex. `rules!="[ 'fulltime' ]"` `rules!="[ val => val.length <= 3 || '最大3文字を使用してください' ]"`     * `reactiverules::Bool` - デフォルトでは、ルールの変更はモデルが変更されるまで新しい検証をトリガーしません; true に設定すると、ルールの変更が検証をトリガーします; パフォーマンスにペナルティがあるため、本当に必要な場合のみ使用してください     * `lazyrules::Union{Bool, String}` - ブール値 true に設定すると、フィールドが最初にフォーカスを失った後にのみ 'rules' に対して検証ステータスをチェックします; 'ondemand' に設定すると、コンポーネントの validate() メソッドが手動で呼び出されたとき、またはラッパー `form` が自分自身を送信するときにのみトリガーされます `true` `false` `ondemand`     * `loading::Bool` - スピナーを表示することで、ユーザーにプロセスが進行中であることを通知します; スピナーは 'loading' スロットを使用してカスタマイズできます。     * `clearable::Bool` - 値（未定義または null でない場合）が設定されると、クリア可能なアイコンを追加します; クリックすると、モデルは null になります     * `autofocus::Bool` - 初期コンポーネントレンダリング時にフィールドにフォーカスを当てます     * `for::String` - コントロールの 'id' と、それをラップするラベルの 'for' 属性を指定するために使用されます; 'name' プロパティが指定されていない場合は、この属性にも使用されます ex. `myFieldsId`
3. コンテンツ     * `errormessage::String` - 検証エラーメッセージ（'error' が 'true' に設定されている場合のみ表示されます） ex. `ユーザー名は少なくとも5文字でなければなりません`     * `noerroricon::Bool` - エラーがある場合にエラーアイコンを非表示にします     * `label::Union{String,Symbol}` - フィールドがフォーカスを得ると、入力フィールドの上に「浮かぶ」テキストラベル ex. `ユーザー名`     * `stacklabel::Bool` - フィールドの内容に関係なく、ラベルは常にフィールドの上に表示されます（もしあれば）     * `hint::String` - ラップされたフォームコンポーネントの下に配置されるヘルパー（ヒント）テキスト ex. `3文字から12文字の間を入力してください`     * `hidehint::Bool` - フィールドがフォーカスを持っていないときにヘルパー（ヒント）テキストを非表示にします     * `prefix::String` - プレフィックス ex. `$`     * `suffix::String` - サフィックス ex. `@gmail.com`     * `loading::Bool` - スピナーを表示することで、ユーザーにプロセスが進行中であることを通知します; スピナーは 'loading' スロットを使用してカスタマイズできます。     * `clearable::Bool` - 値（未定義または null でない場合）が設定されると、クリア可能なアイコンを追加します; クリックすると、モデルは null になります     * `clearicon::String` - クリア可能なアイコンに使用するカスタムアイコン; 指定されていない場合は、デフォルトのアイコンが使用されます     * `labelslot::Bool` - ラベルスロットを有効にします; 'label' プロパティが設定されていない場合は、'label' スロットの強制使用のために設定する必要があります     * `bottomslots::Bool` - ボトムスロット（'error', 'hint', 'counter'）を有効にします     * `counter::Bool` - 右下に自動カウンターを表示します     * `shadowtext::String` - コントロール内のテキストの最後に影として表示されるテキスト; type=file には適用されません     * `autogrow::Bool` - フィールドがその内容に応じて自動的に成長するようにします（textarea を使用）
4. 状態     * `disable::Bool` - コンポーネントを無効モードにします     * `readonly::Bool` - コンポーネントを読み取り専用モードにします
5. スタイル     * `labelcolor::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのラベルの色名; 'color' プロパティをオーバーライドします; 'color' プロパティとの違いは、フィールドがフォーカスされていないときでもラベルは常にこの色を持つことです ex. `primary` `teal`     * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名     * `bgcolor::String` - [カラーパレット](https://quasar.dev/style/color-palette)からの色     * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します     * `filled::Bool` - フィールドに 'filled' デザインを使用します     * `outline::Bool` - フィールドに 'outlined' デザインを使用します     * `borderless::Bool` - フィールドに 'borderless' デザインを使用します     * `standout::Union{Bool, String}` - フィールドに 'standout' デザインを使用します; フォーカス時に適用されるクラスを指定します（デフォルトのものをオーバーライド） ex. `standout` `standout="bg-primary text-white"`     * `hidebottomspace::Bool` - これらが使用されていないときに、ヒント/エラー/カウンターのためのスペースを予約しないようにします; その結果、これらのアニメーションも無効になります; ヒント/エラーエリアがその内容に基づいて垂直に伸びることも許可します     * `rounded::Bool` - コンポーネントの角を小さな標準のボーダー半径で適用します     * `square::Bool` - ボーダー半径を削除してボーダーを四角くします; 'rounded' プロパティをオーバーライドします     * `dense::Bool` - 密なモード; より少ないスペースを占有します     * `itemaligned::Union{Vector, String, Dict}` - 内部コンテンツの整列を `item` のそれに一致させます     * `inputclass::Union{Vector, String, Dict}` - 基本の入力タグに属性を付与するためのクラス定義 ex. `my-special-class` `inputclass!="{ 'my-special-class': <condition> }"`     * `inputstyle::Union{Vector, String, Dict}` - 基本の入力タグに属性を付与するためのスタイル定義 ex. `background-color: #ff0000` `inputstyle!="{ backgroundColor: #ff0000 }"`
6. モデル     * `debounce::Union{String, Int}` - モデルを更新する際のデバウンス量（ミリ秒単位） ex. `0` `500`     * `maxlength::Union{String, Int}` - モデルの最大長を指定します ex. `12`

```
