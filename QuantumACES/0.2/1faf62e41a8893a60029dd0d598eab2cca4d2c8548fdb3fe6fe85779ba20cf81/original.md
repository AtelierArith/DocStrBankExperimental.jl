QuantumACES is a package for designing and simulating scalable and performant Pauli noise characterisation experiments for stabiliser circuits with averaged circuit eigenvalue sampling (ACES). It focuses on the context of quantum error correction and fault-tolerant circuits and, in particular, on the syndrome extraction circuits of topological quantum error correcting codes. It interfaces with [Stim](https://github.com/quantumlib/Stim) for stabiliser circuit simulation, [PyMatching](https://github.com/oscarhiggott/PyMatching) and [BeliefMatching](https://github.com/oscarhiggott/BeliefMatching) for decoding, and [Qiskit](https://github.com/Qiskit/qiskit) for implementation on quantum devices.

The methods used in this package are based on [arXiv:2404.06545](https://arxiv.org/abs/2404.06545) and [arXiv:2502.21044](https://arxiv.org/abs/2502.21044), and they build on the original ACES protocol introduced in [arXiv:2108.05803](https://arxiv.org/abs/2108.05803).

The code for [arXiv:2404.06545](https://arxiv.org/abs/2404.06545) can be found in the `scalable_aces` folder on the [scalable_aces](https://github.com/evanhockings/QuantumACES.jl/tree/scalable_aces) branch.

The code for [arXiv:2502.21044](https://arxiv.org/abs/2502.21044) can be found in the `aces_decoding` folder on the [aces_decoding](https://github.com/evanhockings/QuantumACES.jl/tree/aces_decoding) branch.
