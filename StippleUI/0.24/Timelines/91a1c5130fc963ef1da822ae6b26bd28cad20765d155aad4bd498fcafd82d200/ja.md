```
  timeline(args...; kwargs...)
```

`timeline` コンポーネントは、出来事のリストを時系列で表示します。通常、日付がラベル付けされた長いバーを示すグラフィックデザインであり、通常はその横に出来事が表示されます。タイムラインは、主題やデータに応じて任意の時間スケールを使用できます。      

---

### 例

---

### 表示

```julia-repl
julia> Html.div(class="q-px-lg q-pb-md", [
            timeline(color="secondary", [
            timelineentry("タイムラインの見出し", heading=true),
            timelineentry(title="イベントタイトル", subtitle="1986年2月22日", [
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
            ]),
            timelineentry(title="イベントタイトル", subtitle="1986年2月21日", icon="delete",[
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
            ]),
            timelineentry(title="イベントタイトル",
            subtitle="1986年2月22日",
            avatar="https://cdn.quasar.dev/img/avatar2.jpg", [
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
            ])
            ])
       ])
```

---

### 引数

---

1. 挙動

      * `side::String` - タイムラインエントリを密で快適なレイアウトに配置する側; ゆったりとしたレイアウトの場合は `timelineentry` のサイドプロップによって上書きされます。 (デフォルト: `"right"`) | 例: `"left"` | `"right"`
      * `layout::String` - タイムラインのレイアウト。密はコンテンツとラベルを一方に保持します。快適はコンテンツを一方に、ラベルを反対側に保持します。ゆったりはコンテンツを両側に配置します。 (デフォルト: `"dense"`) | 例: `"comfortable"` | `"loose"` | `"dense"`
2. スタイル

      * `color::String` - Quasar カラーパレットからのコンポーネントの色名。例: `"primary"` | `"teal-10"`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
