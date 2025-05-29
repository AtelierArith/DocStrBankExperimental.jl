```
change_directory(directory::Union{Missing, AbstractString})
```

現在の作業ディレクトリを `directory` に変更します。`directory` が存在しない場合は、作成されます。

`directory` が欠落している場合、デフォルトは `ADCME.PREFIXDIR` です。
