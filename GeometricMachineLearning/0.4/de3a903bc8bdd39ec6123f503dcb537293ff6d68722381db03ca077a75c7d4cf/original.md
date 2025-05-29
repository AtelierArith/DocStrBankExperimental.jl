`NeuralNetworkIntegrator` is a super type of various neural network architectures such as [`SympNet`](@ref) and [`ResNet`](@ref).

The purpose of such neural networks is to approximate the flow of an ordinary differential equation (ODE).

`NeuralNetworkIntegrator`s can be seen as modeling traditional one-step methods with neural networks, i.e. for a fixed time step they perform:

$$
    \mathtt{NeuralNetworkIntegrator}: z^{(t)} \mapsto z^{(t+1)},
$$

to try to approximate the flow of some ODE:

$$
    || \mathtt{Integrator}(z^{(t)}) - \varphi^h(z^{(t)}) || \approx \mathcal{O}(h),
$$

where $\varphi^h$ is the flow map of the ODE for a time step $h$.
