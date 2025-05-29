rescale!(L,k)

$\DeclareMathOperator{\Tr}{Tr}$

Rescale the L-ensemble such that the expected number of samples equals k. The expected number of samples of a DPP equals $\Tr \mathbf{L}\left( \mathbf{L} + \mathbf{I} \right)$. The function rescales $\mathbf{L}$ to $\alpha \mathbf{L}$ such that $\Tr \alpha \mathbf{L}\left( \alpha \mathbf{L} + \mathbf{I} \right) = k$
