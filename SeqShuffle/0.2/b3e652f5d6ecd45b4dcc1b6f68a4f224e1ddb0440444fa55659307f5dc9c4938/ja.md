```
shuffle_fasta(input_fasta_location::String, 
          fasta_output_location::String;
          k::Int=2, seed=nothing,
          max_entries=1000000)
```

入力fastaファイル内の各配列をシャッフルし、各配列内のk-メルの頻度を保持します。

入力:

  * `input_fasta_location`: fastaファイルの絶対ファイルパス。
  * `fasta_output_location`: 出力fastaファイルの絶対ファイルパス。
  * `k`: k-メル頻度のためのk。
  * `seed`: 擬似乱数生成器のためのシード。
  * `max_entries`: fastaファイルから取得する最大エントリ数（1からmax_entriesまで）。

出力: 入力fastaファイルのシャッフル版を含むfastaファイル。
