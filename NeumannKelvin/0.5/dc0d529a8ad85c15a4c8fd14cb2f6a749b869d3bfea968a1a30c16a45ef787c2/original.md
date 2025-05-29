influence(panels;kwargs...) = ∂ₙϕ.(panels,panels';kwargs...) = A

Normal velocity influence matrix.  Computation is accelerated with multi-threading when `Threads.nthreads()>1`.
