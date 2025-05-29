```
ClimaODEFunction(; T_imp!, [dss!], [cache!], [cache_imp!])
ClimaODEFunction(; T_exp!, T_lim!, [T_imp!], [lim!], [dss!], [cache!], [cache_imp!])
ClimaODEFunction(; T_exp_lim!, [T_imp!], [lim!], [dss!], [cache!], [cache_imp!])
```

タイムステップを進めるために使用されるすべての関数のコンテナ:     - `T_imp!(T_imp, u, p, t)`: 暗黙の傾向を設定します     - `T_exp!(T_exp, u, p, t)`: リミッターを通さない明示的傾向の成分を設定します     - `T_lim!(T_lim, u, p, t)`: リミッターを通る明示的傾向の成分を設定します     - `T_exp_lim!(T_exp, T_lim, u, p, t)`: 別々の関数 `T_exp!` と `T_lim!` の融合代替です     - `lim!(u, p, t, u_ref)`: 明示的傾向成分 `T_lim!` によって `u_ref` から増分されたすべての状態 `u` にリミッターを適用します     - `dss!(u, p, t)`: 暗黙のソルバー内で生成された中間状態を除くすべての状態 `u` に直接剛性総和を適用します     - `cache!(u, p, t)`: 最初のタイムステップ前およびその後のすべてのタイムステッピング段階で状態 `u` を反映するようにキャッシュ `p` を更新します     - `cache_imp!(u, p, t)`: 暗黙のソルバー内で `T_imp!` とそのヤコビアンを評価するために必要なキャッシュ `p` の成分を更新します デフォルトでは、`lim!`、`dss!`、および `cache!` はすべて何もしないことになっており、`cache_imp!` は `cache!` と同じです。傾向関数のいずれかを `nothing` に設定することで、統合器内の対応する割り当てを回避できます。
