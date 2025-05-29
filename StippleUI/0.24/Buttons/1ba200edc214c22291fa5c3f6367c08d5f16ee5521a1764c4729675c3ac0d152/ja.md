```
btntoggle(fieldname::Symbol, args...; options::Union{Symbol, Vector{<:AbstractDict}}, kwargs...)
```

---

### 例

---

### モデル

```julia-repl
julia> @app begin
           @in network = :google
           @in networks = [Stipple.opts(label = x, value = Symbol(lowercase(x))) for x in ["Google", "Facebook", "Twitter", "Pinterest", "Reddit"]]
       end
```

### ビュー

```julia-repl
julia> btntoggle(:network, options = :networks, label="Social Networks", rounded = true, color = "white", textcolor= "primary")
"<q-btn-toggle color=\"white\" rounded v-model=\"network\" label=\"Social Networks\" :options=\"networks\" text-color=\"primary\"></q-btn-toggle>"
```

---

### 引数

---

1. 挙動

      * `name::String` - コントロールの名前を指定するために使用されます; フォームを扱う場合に便利です; 指定されていない場合は、存在する場合は 'for' プロパティの値を取ります ex. `car-id` `car-id`
2. コンテンツ

      * `tablecolspan::Union{Int, String}` - テーブルの列数 (table-layout: fixed を使用する場合に必要です) ex. `tablecolspan="12"`
      * `spread::Bool`- 利用可能なスペース全体に水平に広がります
      * `no-caps::Bool`- ラベルテキストを大文字に変換しない (デフォルトではそうなります)
      * `no-wrap::Bool`- ラベルテキストの折り返しを避けます
      * `stack::Bool`- アイコンとラベルを同じ行ではなく垂直にスタックします (デフォルトではそうなっています)
      * `stretch::Bool`- フレックスボックスの親で使用されると、ボタンは親の高さに合わせて伸びます
3. モデル

      * `options::Vector` - ユーザーが選択できる利用可能なオプション。パフォーマンスを最適化するためにオプションのリストを固定します ex. `options=[ "BMW", "Samsung Phone" ]`
      * `clearable::Bool` - すでに選択されたボタンをクリックするとモデルをクリアします
4. 状態

      * `disable::Bool` - コンポーネントを無効モードにします
      * `readonly::Bool` - コンポーネントを読み取り専用モードにします
5. スタイル

      * `color::String` - Quasar カラーパレットからのコンポーネントの色名
      * `text-color::String` - テキスト色をオーバーライドします (必要に応じて); Quasar カラーパレットからの色名
      * `toggle-color::String` - Quasar カラーパレットからのコンポーネントの色名
      * `toggle-text-color::String` - テキスト色をオーバーライドします (必要に応じて); Quasar カラーパレットからの色名
      * `outline::Boolean` - 'outline' デザインを使用します
      * `flat::Boolean` - 'flat' デザインを使用します
      * `unelevated::Boolean` - シャドウを削除します
      * `rounded::Boolean` - 四角い形のボタンに対してより目立つボーダー半径を適用します
      * `push::Boolean` - 'push' デザインを使用します
      * `glossy::Boolean` - 光沢効果を適用します
      * `size::String` - ボタンサイズ名または単位名を含む CSS 単位
      * `padding::String` - カスタムパディングを適用します (垂直 [水平]); CSS 単位でのサイズ、単位名または標準サイズ名 (none|xs|sm|md|lg|xl) を含みます; 設定すると最小幅と高さも削除されます
      * `ripple::Union{Boolean, Dict}``- マテリアルリップルを設定します ( 'false' に設定することで無効にするか、Dict を供給します, 例.`Stipple.opts(early = true, center = true, color = "teal", keyCodes = [])`)
      * `dense::Boolean` - 密なモード; より少ないスペースを占有します

```
