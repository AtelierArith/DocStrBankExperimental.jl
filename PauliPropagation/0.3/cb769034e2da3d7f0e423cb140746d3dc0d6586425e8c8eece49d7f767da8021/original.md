```
tomatrix(gate::PauliRotation, theta)
```

Compute the unitary matrix for the `PauliRotation` gate with parameter `theta` in the computational 0/1 basis. This is done by computing the matrix `U = cos(θ/2) I - i sin(θ/2) P` where `P` is the Pauli matrix corresponding to the `symbols`. The returned unitary is returned in Schrödinger picture form. 
