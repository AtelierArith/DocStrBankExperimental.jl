この関数は、任意のグレーデッドポセット P に対して、次元 k=0,..,maxdim の組合せラプラシアンを計算します。

使用例:

Laps=Laplacians(Δ); # ここで Δ は単体複体です Laps=Laplacians(P); # ここで P はグレーデッドポセットです Laps=Laplacians(D); # ここで D は有向複体です

ここで Laps[d+1] は次元 d=0 から始まる d 次元チェーンに作用するラプラシアンです。返される行列 Laps[d+1] はスパースで整数値です。組合せラプラシアンは「非縮約」(コ-)ホモロジー演算子に対して計算されます。
