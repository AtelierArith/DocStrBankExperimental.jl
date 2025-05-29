`solve(hamiltonian::Hamiltonian, basisset::BasisSet)`

この関数は、固有値 $E$ と固有ベクトル $\pmb{c}$ を返します。

$$
\pmb{H} \pmb{c} = E \pmb{S} \pmb{c}.
$$

ハミルトニアン行列は $H_{ij} = \langle \phi_{i} | \hat{H} | \phi_{j} \rangle$ と定義されます。重なり行列は $S_{ij} = \langle \phi_{i} | \phi_{j} \rangle$ と定義されます。
