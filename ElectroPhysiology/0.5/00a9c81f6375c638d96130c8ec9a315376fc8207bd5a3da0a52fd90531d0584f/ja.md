```
parseABF(super_folder::String; extension::String=".abf")
```

ディレクトリとそのサブディレクトリ内のABFファイルを再帰的に検索します。

# 引数

  * `super_folder`: 検索を開始するルートディレクトリ
  * `extension`: 検索するファイル拡張子（デフォルト: ".abf"）

# 戻り値

  * 見つかったすべてのABFファイルへのファイルパスのベクター

# 例

```julia
# 現在のディレクトリとサブディレクトリ内のすべてのABFファイルを見つける
files = parseABF(".")

# カスタム拡張子のファイルを見つける
files = parseABF("data/", extension=".dat")

# 複数のファイルを処理する
for file in parseABF("experiment_data/")
    exp = readABF(Float32, file)
    process_experiment(exp)
end
```

# 例外

  * `ArgumentError`: ディレクトリ内に一致するファイルが見つからない場合

参照: [`readABF`](@ref)
