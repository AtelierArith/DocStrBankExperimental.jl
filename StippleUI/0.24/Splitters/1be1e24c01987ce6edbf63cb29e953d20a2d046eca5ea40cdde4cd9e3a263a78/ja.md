```
splitter(fieldname::Symbol, args...; kwargs...)
```

---

### 例

---

### モデル

```julia-repl
julia> @vars SplitterModel begin
            splitterM::R{Int} = 50
       end
```

### ビュー

```julia-repl
julia> splitter(:splitterM, style="height: 400px", [
        template("", "v-slot:before", [
          Html.div(class="q-pa-md", [
            Html.div("Before", class="text-h4 q-mb-md"),
            Html.div("{{ n }}. Lorem ipsum dolor sit, amet consectetur adipisicing elit.
               Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus
               obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.",
              class = "q-my-md",
              @for(:"n in 20"), key! = "n")
          ])
        ]),
        template("", "v-slot:after", [
          Html.div(class="q-pa-md", [
            Html.div("After", class="text-h4 q-mb-md")
              Html.div("{{ n }}. Lorem ipsum dolor sit, amet consectetur adipisicing elit.
               Quis praesentium cumque magnam odio iure quidem, quod illum numquam possimus
               obcaecati commodi minima assumenda consectetur culpa fuga nulla ullam. In, libero.",
              class = "q-my-md",
              @for(:"n in 20"), key! = "n")
          ])
        ])
       ])
```

---

### 引数

---

1. コンテンツ

      * `horizontal::Bool` - スプリッターが2つのパネルを垂直ではなく水平に分割できるようにします
      * `limits::Vector` - 2つのパネルの最小および最大分割サイズを表す2つの値の配列; 'px'単位が設定されている場合、他の側で無制限にするためにInfinityを2番目の値として使用できます
2. モデル

      * `reverse::Bool` - モデルサイズを2番目のパネルに適用します（デフォルトでは最初のパネルに適用されます）
      * `unit::String` - モデルのCSS単位
      * `emitimmediately::Bool` - ユーザーがセパレーターをパンしている間にモデルを発信します
      * `limits::Vector` - 2つのパネルの最小および最大分割サイズを表す2つの値の配列; 'px'単位が設定されている場合、他の側で無制限にするためにInfinityを2番目の値として使用できます
3. 状態

      * `disable::Bool` - コンポーネントを無効モードにします
4. スタイル

      * `classbefore::Union{Vector,String,Dict}` - 'before'パネルに割り当てるクラス定義 ex. `"bg-deep-orange"`
      * `classafter::Union{Vector,String,Dict}` - 'after'パネルに割り当てるクラス定義 ex. `"bg-deep-orange"`
      * `separatorclass::Union{Vector,String,Dict}` - スプリッターセパレーターに割り当てるクラス定義 ex. `"bg-deep-orange"`
      * `separatorstyle::Union{Vector,String,Dict}` - スプリッターセパレーターに割り当てるスタイル定義 ex. `"border-color: #ff0000;"`
      * `dark::Bool` - セパレーターにデフォルトの明るい色を適用します; 背景が暗い場合に使用します; separator-classまたはseparator-styleプロパティをオーバーライドする場合は使用を避けてください

```
