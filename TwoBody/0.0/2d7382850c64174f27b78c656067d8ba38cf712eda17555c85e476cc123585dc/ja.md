`optimize(hamiltonian::Hamiltonian, basisset::GeometricBasisSet; perturbation=Hamiltonian(), info=4, optimizer=Optim.NelderMead())`

この関数は、Optim.jlを使用して$r_1$と$r_n$を最適化することによってエネルギーを最小化します。

$$
\frac{\partial E}{\partial r_1} = \frac{\partial E}{\partial r_n} = 0
$$
