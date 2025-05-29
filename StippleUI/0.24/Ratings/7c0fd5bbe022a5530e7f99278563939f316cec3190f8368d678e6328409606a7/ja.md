```
rating(fieldname::Union{Symbol,Nothing} = nothing,args...; kwargs...)
```

Ratingは、ユーザーがアイテムを評価できるコンポーネントで、通常「星評価」として知られています。

---

### 例

---

### モデル

```julia-repl
julia> @vars RatingModel begin
          myrating::R{Int} = 3
       end

```

### ビュー

```julia-repl
julia> rating(:myrating,size="1.5em",icon="thumb_up")
julia> rating(:myrating, size="2em",color="red-7",icon="favorite_border")
julia> rating(:myrating, size="2.5em", color="purple-4", icon="create")
```

---

### 引数

---

1. 挙動

      * `name::String` - コントロールの名前を指定するために使用されます; URL `car_id` に直接送信されるフォームを扱う場合に便利です
2. コンテンツ

      * `icon::Union{String, Vector}` - アイコン名; 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 配列が提供される場合、各評価値は配列内の対応するアイコンを使用します (0ベース) 例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `iconselected::Union{String, Vector}` - 選択時に使用されるアイコン名 (オプション); 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 配列が提供される場合、各評価値は配列内の対応するアイコンを使用します (0ベース) 例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      * `iconhalf::Union{String, Vector}` - 選択時に使用されるアイコン名 (オプション); 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 配列が提供される場合、各評価値は配列内の対応するアイコンを使用します (0ベース) 例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
3. ラベル

      * `max::Union{Int, String}` - 表示するアイコンの数 例: `3` `max="5"`
4. モデル

      * `noreset::Bool` - 使用時、現在のモデル値を0にリセットするアイコンのクリック/タップのデフォルト動作を無効にします
5. 状態

      * `readonly::Bool` - コンポーネントを読み取り専用モードにします
      * `disable::Bool` - コンポーネントを無効モードにします
6. スタイル

      * `size::String` - CSS単位でのサイズ、単位名または標準サイズ名 (xs|sm|md|lg|xl) を含む 例: `16px` `2rem` `md` `xs`
      * `color::Union{String, Vector}` - [カラーパレット](https://quasar.dev/style/color-palette) からのコンポーネントの色名; v1.5.0+: 配列が提供される場合、各評価値は配列内の対応する色を使用します (0ベース) 例: `primary` `primary` `teal-10` `["accent", "grey-7"]`
      * `colorselected::Union{String, Vector}` - 選択されたアイコンのためのQuasarパレットからの色名 `primary` `teal-10`
      * `colorhalf::Union{String, Vector}` - [カラーパレット](https://quasar.dev/style/color-palette) からの色名 例: `primary` `teal-10`
      * `nodimming::Bool` - 選択されていないアイコンの不透明度を下げません

```
