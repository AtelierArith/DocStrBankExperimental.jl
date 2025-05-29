contains(s::Simplex, pt; atol=0., rtol=defaulrtol(eltype(pt)))

単純体内に点が含まれているかどうかを確認します。単純体の内因次元が周囲の空間の次元よりも小さい場合（例えば、3Dの三角形）、atolおよびrtolパラメータが必要です。
