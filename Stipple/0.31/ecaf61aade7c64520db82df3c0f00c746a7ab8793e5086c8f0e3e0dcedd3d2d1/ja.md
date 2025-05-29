```markdown
Vueコンポーネントのフィールドにバインドされたjs式を作成します。内部的にはこれはSymbolへの変換に過ぎませんが、スペースを含むシンボルを作成するための短いバージョンです。

### 例

```

julia> btn("", @click("toggleFullscreen"), icon = R"is*fullscreen ? 'fullscreen*exit' : 'fullscreen'") "<q-btn label v-on:click="toggleFullscreen" :icon="is*fullscreen ? 'fullscreen*exit' : 'fullscreen'"></q-btn>"

```

注意: 変数名のみを含む式の場合、Symbol表記を推奨します。

```

julia> btn("", @click("toggleFullscreen"), icon = :fullscreen*icon) "<q-btn label v-on:click="toggleFullscreen" :icon="fullscreen*icon"></q-btn>"

```

```
