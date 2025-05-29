コードをすべてのスレッドで別々に [`Marker.startregion`](@ref) と [`Marker.stopregion`](@ref) で囲むための便利なマクロです。

# 例

```julia
julia> using LIKWID

julia> Marker.init()

julia> @parallelmarker begin
           Threads.@thread :static for i in 1:Threads.nthreads()
               # スレッドローカル計算
           end
       end

julia> Marker.close()

```
