```
CodeEditor(language::String; initial_source="", theme="chrome", editor_options...)
```

Defaults for `editor_options`:

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

The content of the editor (as a string) is updated in `editor.onchange::Observable`.
