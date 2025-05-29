influence(panels;kwargs...) = ∂ₙϕ.(panels,panels';kwargs...) = A

法線速度影響行列。`Threads.nthreads()>1` の場合、計算はマルチスレッドで加速されます。
