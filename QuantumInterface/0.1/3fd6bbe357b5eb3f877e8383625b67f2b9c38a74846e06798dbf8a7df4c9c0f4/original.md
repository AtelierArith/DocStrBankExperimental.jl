Base class for all super operator classes.

Super operators are bijective mappings from operators given in one specific basis to operators, possibly given in respect to another, different basis. To embed super operators in an algebraic framework they are defined with a left hand basis `basis_l` and a right hand basis `basis_r` where each of them again consists of a left and right hand basis.

$$
A_{bl_1,bl_2} = S_{(bl_1,bl_2) ↔ (br_1,br_2)} B_{br_1,br_2}
\\
A_{br_1,br_2} = B_{bl_1,bl_2} S_{(bl_1,bl_2) ↔ (br_1,br_2)}
$$
