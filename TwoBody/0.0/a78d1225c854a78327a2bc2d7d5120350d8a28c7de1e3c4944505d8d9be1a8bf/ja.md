`function optimize(hamiltonian::Hamiltonian, basisset::BasisSet; perturbation=Hamiltonian(), info=4, progress=true, optimizer=Optim.NelderMead(), options...)`

この関数は、Optim.jlを使用して基底関数の指数を変更することによってエネルギーを最小化します。

$$
\frac{\partial E}{\partial a_i} = 0
$$
