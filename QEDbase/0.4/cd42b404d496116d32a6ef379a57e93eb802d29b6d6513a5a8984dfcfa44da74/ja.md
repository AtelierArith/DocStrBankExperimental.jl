```
number_particles(proc_def::AbstractProcessDefinition, dir::ParticleDirection)
```

与えられた方向に応じて[`number_incoming_particles`](@ref)または[`number_outgoing_particles`](@ref)にディスパッチする便利な関数で、入射粒子または出射粒子の数をそれぞれ返します。
