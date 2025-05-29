```
add!(psum1::PauliSum, psum2::PauliSum)
```

Add two `PauliSum`s `psum1` and `psum2`. Changes `psum1` in-place. `psum1` and `psum2` need to be defined on the same number of qubits and have the same coefficient type.
