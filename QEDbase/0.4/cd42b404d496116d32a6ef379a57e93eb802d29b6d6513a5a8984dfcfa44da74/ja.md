```
number_particles(proc_def::AbstractProcessDefinition, dir::ParticleDirection)
```

与えられた方向に応じて[`number_incoming_particles`](@ref)または[`number_outgoing_particles`](@ref)にディスパッチする便利な関数で、入ってくる粒子または出ていく粒子の数をそれぞれ返します。
