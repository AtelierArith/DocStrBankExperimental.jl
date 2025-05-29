```
tabpanelgroup(args...; kwargs...)
```

`tabpanelgroup` は、ウィンドウのスペースを節約しながら、より多くの情報を表示する方法です。

---

### 例

---

### モデル

```julia-repl
julia> @vars TabPanelModel begin
            gpanel::R{String} = "panel"
       end
```

### ビュー

```julia-repl
julia> Html.div(class="q-pa-md", [
          Html.div(class="q-gutter-y-md", style="max-width: 350px", [
             tabpanelgroup(:gpanel, animated=true, swipeable=true, infinite=true,
                   class="bg-purple text-white shadow-2 rounded-borders", [
                   tabpanel("Lorem ipsum dolor sit amet consectetur
                    adipisicing elit.", name="mails", [
                   Html.div("Mails", class="text-h6")
             ]),
            
             tabpanel("Lorem ipsum dolor sit amet consectetur
                  adipisicing elit.", name="alarms", [
                        Html.div("Alarms", class="text-h6")
             ]),

             tabpanel("Lorem ipsum dolor sit amet consectetur
                  adipisicing elit.", name="movies", [
                        Html.div("Movies", class="text-h6")
                  ]),
             ])
          ])
       ])
```

---

### 引数

---

1. 挙動

      * `keepalive::Bool` - コンテンツに Vue のネイティブ <keep-alive> コンポーネントを使用するのと同等
      * `keepaliveinclude::Union{String,Vector}` - <keep-alive> のための Vue のネイティブ include プロパティを使用するのと同等; 値は有効な Vue コンポーネント名でなければならない (例: `"a,b"` `"/a|b/"` `['a', 'b']`)
      * `keepaliveexclude::Union{String,Vector}` - <keep-alive> のための Vue のネイティブ exclude プロパティを使用するのと同等; 値は有効な Vue コンポーネント名でなければならない (例: `"a,b"` `"/a|b/"` `['a', 'b']`)
      * `keepalivemax::Int` - <keep-alive> のための Vue のネイティブ max プロパティを使用するのと同等 (例: `2`)
      * `animated::Bool` - パネル間の遷移を有効にする (「transition-prev」と「transition-next」プロパティも参照)
      * `infinite::Bool` - コンポーネントを無限に表示させる (最後のパネルに達したとき、次のパネルが最初のパネルになる)
      * `swipeable::Bool` - スワイプイベントを有効にする (コンテンツのタッチ/マウスイベントに干渉する可能性がある)
      * `vertical::Bool` - デフォルトの遷移とスワイプアクションは垂直軸で行われる
      * `transitionprev::String` - Quasar の組み込み遷移の一つ (「animated」プロパティが設定されている場合のみ効果がある) (例: `"fade"` `"slide-down"`)
      * `transitionnext::String` - Quasar の組み込み遷移の一つ (「animated」プロパティが設定されている場合のみ効果がある) (例: `"fade"` `"slide-down"`)
