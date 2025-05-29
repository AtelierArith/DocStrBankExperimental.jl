internal data required used solving an ac power flow

the primary use of this data structure is to prevent re-allocation of memory between successive power flow solves

  * `data` – a power models data dictionary
  * `bus_gens` – for each bus id, a list of active generators
  * `am` – an admittance matrix computed from the data dictionary
  * `bus_type_idx` – bus types (i.e., 1, 2, 3)
  * `p_delta_base_idx` – fixed active power delta at a bus
  * `q_delta_base_idx` – fixed reactive power delta at a bus
  * `p_inject_idx` – variable active power generator injection at a bus
  * `q_inject_idx` – variable reactive power generator injection at a bus
  * `vm_idx` – variable voltage magnitude at a bus
  * `va_idx` – variable voltage angle at a bus
  * `neighbors` – neighboring buses to a given bus
  * `x0` – 2*|N| variables, one for each bus, varies based on bus type
  * `F0` – 2*|N| bus power balance evaluation values, active power followed by reactive power
  * `J0` – a sparse matrix holding the Jacobian of the F0 power balance evaluation function

The postfix `_idx` indicates the admittance matrix indexing convention.
