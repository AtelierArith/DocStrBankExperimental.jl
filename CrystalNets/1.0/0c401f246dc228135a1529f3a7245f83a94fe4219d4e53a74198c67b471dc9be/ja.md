```
CrystalNets.jl
```

結晶ネットトポロジーの自動認識のためのモジュール。実行可能ファイルとして使用するには、シェルでソースファイルを実行します：

```bash
julia --project=/path/to/CrystalNets/ /path/to/CrystalNets/src/CrystalNets.jl
```

そうでない場合、モジュールとして、化学ファイル形式で与えられた結晶の基盤となるネットを認識するために、エントリーポイントは次の実行です：

```julia
julia> using CrystalNets

julia> determine_topology(FILE)
```

CrystalNets.jlの使用方法や、起動時のレイテンシを減らすための完全なインストール方法については、https://coudertlab.github.io/CrystalNets.jl/ のドキュメントを参照してください。
