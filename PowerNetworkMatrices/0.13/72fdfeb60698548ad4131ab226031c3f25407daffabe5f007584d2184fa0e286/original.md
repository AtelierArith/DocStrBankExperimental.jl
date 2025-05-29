Nodal admittance matrix (Ybus) is an N x N matrix describing a power system with N buses. It represents the nodal admittance of the buses in a power system.

The Ybus Struct is indexed using the Bus Numbers, no need for them to be sequential

The fields yft and ytf are the branch admittance matrices for the from-to and to-from branch admittances respectively. The rows correspond to branches and the columns to buses. The matrix columns are mapped to buses using fb, tb arrays of the matrix columns that correspond to the `from` and `to` buses.  Using yft, ytf, and the voltage vector, the branch currents and power flows can be calculated.
