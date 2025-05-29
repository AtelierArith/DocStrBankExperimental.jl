```
fluid = VdWFluid(fluid)
```

`fluid::Symbol`のファイルプロパティからのバン・デル・ワールス定数を読み込み、完全な`VdWFluid`データ構造を返します。***注意: VdW*fluid*props.csvの最後の3行のコメントを削除しないでください。

# 引数

  * `fluid::Symbol`: VdWFluid構造体を構築したい流体

# 戻り値

  * `VdWFluid::struct`: バン・デル・ワールス定数を含むデータ構造
