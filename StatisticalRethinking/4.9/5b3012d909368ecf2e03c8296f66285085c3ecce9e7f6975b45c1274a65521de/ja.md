# sr_datadir

StatisticalRethinkingのsrc/ディレクトリを使用した相対パス。

### StatisticalRethinking内の`Howell1.csv`にアクセスする例:

```julia
df = CSV.read(sr_datadir("Howell1.csv"), DataFrame)
```
