```
CodeEditor(language::String; initial_source="", theme="chrome", editor_options...)
```

`editor_options`のデフォルト:

```
(
    autoScrollEditorIntoView = true,
    copyWithEmptySelection = true,
    wrapBehavioursEnabled = true,
    useSoftTabs = true,
    enableMultiselect = true,
    showLineNumbers = false,
    fontSize = 16,
    wrap = 80,
    mergeUndoDeltas = "always"
)
```

エディタの内容（文字列として）は`editor.onchange::Observable`で更新されます。
