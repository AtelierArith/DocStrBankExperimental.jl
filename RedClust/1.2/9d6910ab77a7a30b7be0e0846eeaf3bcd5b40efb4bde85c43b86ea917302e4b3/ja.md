adjacencymatrix(clusts::ClustLabelVector) -> Matrix{Bool} は、与えられたクラスタラベルベクター `clusts` に対応する `n`×`n` 隣接行列を返します。ここで、`n = length(clusts)` です。
