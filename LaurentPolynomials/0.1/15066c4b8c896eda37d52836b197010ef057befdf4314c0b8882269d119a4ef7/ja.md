`Pol(c::AbstractVector,v::Integer=0;check=true,copy=true)`

評価 `v` を持つ多項式を係数 `c` で作成します。

その後、`check` が `false` でない限り、`c` に先頭または末尾のゼロがないことを確認することで結果を正規化します（この状態であることが確実でない限り `check=false` に設定しないでください）。

`copy=false` でない限り、`c` の内容はコピーされます（内容を共有できることがわかっている場合は `copy=false` に設定することで、1 回のアロケーションを削減できます）。
