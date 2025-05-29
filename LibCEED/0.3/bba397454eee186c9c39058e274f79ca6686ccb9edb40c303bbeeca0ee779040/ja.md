```
CopyMode
```

`COPY_VALUES`、`USE_POINTER`、または `OWN_POINTER` のいずれか。

`OWN_POINTER` は、Julia で作成されたオブジェクトには通常サポートされていません。なぜなら、それらはガーベジコレクタによって破棄される必要があり、C から解放することはできないからです。
