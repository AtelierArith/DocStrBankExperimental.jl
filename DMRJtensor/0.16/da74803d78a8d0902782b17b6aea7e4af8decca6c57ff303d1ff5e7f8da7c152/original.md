```
ox,oy,oz,op,om,Rx,Ry,Rz,H,O,Id = qubits([,d=2,angle=pi/4])
```

Creates a set of Pauli operators for a certain number of states `d` and angle for a rotation gate `angle`

#Outputs:

  * `ox`: Pauli-x operator
  * `oy`: Pauli-y operator
  * `oz`: Pauli-z operator
  * `op`: raising operator
  * `om`: lowering operator
  * `Rx`: rotation of x-axis operator
  * `Ry`: rotation of y-axis operator
  * `Rz`: rotation of z-axis operator
  * `H`: Hadamard gate
  * `O`: zero matrix
  * `Id`: identity matrix
