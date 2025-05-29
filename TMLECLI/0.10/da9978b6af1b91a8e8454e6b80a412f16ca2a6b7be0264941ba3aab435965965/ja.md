```
make_summary(
    prefix; 
    outputs=Outputs(json=JSONOutput(filename="summary.json"))
)
```

複数のTMLE .hdf5出力ファイルを1つのファイルに結合します。複数のフォーマットを同時に出力できます。

# 引数

  * `prefix`: サマリーファイルを作成するために使用される.hdf5ファイルのプレフィックス

# オプション

  * `-o, --outputs`: 出力設定。
