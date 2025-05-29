ランク0では、この関数は `Dict{Int, Vector{Int}}` を返します。ここで、キーはMPIランクIDであり、値は現在MPIランクのJuliaスレッドを実行しているCPUスレッドのCPU IDです。他のすべてのランクでは `nothing` を返します。
