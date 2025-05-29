Compute the two-part date format used by SOFA.jl functions forr a given Epoch.

Arguments:

  * `epc::Epoch`: Epoch
  * `tsys::String`: Time system to return output in

Returns:

  * `d1::Real`: First part of two part date. [days]
  * `d2::Real`: Second part of two part date. [days]
