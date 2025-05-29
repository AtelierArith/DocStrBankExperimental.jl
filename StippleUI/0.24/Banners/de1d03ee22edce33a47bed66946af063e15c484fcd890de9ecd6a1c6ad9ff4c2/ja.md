```
banner(content::String = "", args...; buttons::Vector{String} = String[], icon::Union{String,Nothing} = nothing, kwargs...)
```

`banner` コンポーネントは、目立つメッセージと関連するオプションのアクションを表示するためのバナー要素を作成します。

Material Design の仕様によれば、バナーは「画面の上部、トップアプリバーの下に表示されるべき」とされていますが、もちろん、`dialog` の中など、意味のある場所にどこにでも配置できます。

---

### 例

---

### 表示

```julia-repl
julia> banner("残念ながら、クレジットカードが通過しませんでした。再試行してください。", class="bg-primary text-white", [
          template("", "v-slot:action", [
            btn("閉じる", flat=true, color="white"),
            btn("クレジットカードを更新", flat=true, color="white")
          ])
       ])
       
julia> banner("旅行データを取得できませんでした。", rounded=true, class="bg-grey-3", [
          template("", "v-slot:avatar", [
            imageview(src="https://cdn.quasar.dev/img/mountains.jpg", style="width: 100px; height:64px")
          ]),
          template("", "v-slot:action", [
            btn("再試行", flat=true, color="white")
          ])
       ])
```

---

### 引数

---

1. コンテンツ

      * `inlineactions::Bool` - コンテンツと同じ行にアクションを表示する
2. スタイル

      * `dense::Bool` - 密なモード; より少ないスペースを占有
      * `rounded::Bool` - コンポーネントの角を小さな標準のボーダー半径で丸める
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知する
