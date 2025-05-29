```
@__FILEPATH__ -> SystemPath
```

@**FILEPATH** は、マクロを含むファイルの絶対ファイルパスを持つパスに展開されます。REPLから実行された場合や、julia -e <expr> によって評価された場合は、空のPathを返します。
