```
constraint_mc_load_power(pm::LPUBFDiagModel, load_id::Int; nw::Int=nw_id_default, report::Bool=true)
```

Delta/voltage-dependent load models for LPUBFDiagModel. Delta loads use the auxilary power variable (X). The constant current load model is derived by linearizing around the flat-start voltage solution.

$$
\begin{align}
&\text{Constant power:} \Rightarrow P_i^d = P_i^{d0},~Q_i^d = Q_i^{d0} ~\forall i \in L \\
&\text{Constant impedance (Wye):} \Rightarrow P_i^d = a_i \cdot w_i,~Q_i^d = b_i \cdot w_i ~\forall i \in L \\
&\text{Constant impedance (Delta):} \Rightarrow P_i^d = 3\cdot a_i \cdot w_i,~Q_i^d = 3\cdot b_i \cdot w_i ~\forall i \in L \\
&\text{Constant current (Wye):} \Rightarrow P_i^d = \frac{a_i}{2}\cdot \left( 1+w_i \right),~Q_i^d = \frac{b_i}{2}\cdot \left( 1+w_i \right) \forall i \in L \\
&\text{Constant current (Delta):} \Rightarrow P_i^d = \frac{\sqrt{3} \cdot a_i}{2}\cdot \left( 1+w_i \right),~Q_i^d = \frac{\sqrt{3} \cdot b_i}{2}\cdot \left( 1+w_i \right) \forall i \in L
\end{align}
$$
