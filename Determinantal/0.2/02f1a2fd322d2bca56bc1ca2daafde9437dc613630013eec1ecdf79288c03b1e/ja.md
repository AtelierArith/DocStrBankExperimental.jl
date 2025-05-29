rescale!(L,k)

$$
\DeclareMathOperator{\Tr}{Tr}
$$

L-アンサンブルを再スケールして、期待されるサンプル数がkに等しくなるようにします。DPPの期待されるサンプル数は$\Tr \mathbf{L}\left( \mathbf{L} + \mathbf{I} \right)$に等しいです。この関数は、$\Tr \alpha \mathbf{L}\left( \alpha \mathbf{L} + \mathbf{I} \right) = k$となるように$\mathbf{L}$を$\alpha \mathbf{L}$に再スケールします。
