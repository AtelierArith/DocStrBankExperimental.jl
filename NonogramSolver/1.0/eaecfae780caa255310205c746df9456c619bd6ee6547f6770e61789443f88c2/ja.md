```
read_puzzle_from_cwc(cwcFileName::String) -> Puzzle
```

[Web Paint-by-Number](https://webpbn.com/export.cgi) から .CWC ファイルとしてエクスポートされたパズルをインポートします。

# 例

`puzzle.cwc` を Web Paint-by-Number からエクスポートし、作業ディレクトリに配置した後、次のように構築できます：

```julia
puzzle = read_puzzle_from_cwc("puzzle.cwc")
```
