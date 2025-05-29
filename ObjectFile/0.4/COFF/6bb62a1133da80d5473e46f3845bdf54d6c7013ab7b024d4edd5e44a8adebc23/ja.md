```
COFFRPath
```

COFF RPathオブジェクト; COFFファイルにはその中にRPathがないことに注意してくださいが、読み込まれるバイナリと同じディレクトリ（例: `$ORIGIN`）を*検索*します。これを実現するために`COFFRPath`を使用しますが、厳密に言えば「COFF RPath」というものは存在しません。
