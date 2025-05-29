```
struct Individuals{T,N}
```

  * Data:           📌 (position),   🔴(record), 🆔 (ID), P (`FlowFields`)
  * Functions:      🚄 (velocity),   ∫ (integration), 🔧(postprocessing)
  * NamedTuples:    D (diagnostics),      M (metadata)

The velocity function 🚄 typically computes velocity at individual positions (📌 to start) within the  specified space-time domain by interpolating gridded variables (provided via P). Individual trajectories  are computed by integrating (∫) interpolated velocities through time. Normally, integration is done by  calling ∫! which updates 📌 at the end and records results in 🔴 via 🔧. Ancillary data, for use in  🔧 for example, can be provided in D and metadata stored in M.

Unicode cheatsheet:

  * 📌=`\:pushpin:<tab>`,          🔴=`\:red_circle:<tab>`, 🆔=`\:id:<tab>`
  * 🚄=`\:bullettrain_side:<tab>`, ∫=`\int<tab>`,          🔧=`\:wrench:<tab>`
  * P=`\itP<tab>`,                 D=`\itD<tab>`,           M=`\itM<tab>`

Simple constructors that use `FlowFields` to choose adequate defaults:

  * Individuals(F::uvArrays,x,y)
  * Individuals(F::uvwArrays,x,y,z)
  * Individuals(F::uvMeshArrays,x,y,fid)
  * Individuals(F::uvwMeshArrays,x,y,z,fid)

Further customization is achievable via keyword constructors:

```
df=DataFrame( ID=[], x=[], y=[], z=[], t = [])
I=Individuals{Float64,2}(📌=zeros(3,10),🆔=1:10,🔴=deepcopy(df))
I=Individuals(📌=zeros(3,2),🆔=collect(1:2),🔴=deepcopy(df))
```

Or via the plain text (or no-unicode) constructors:

```
df=DataFrame( ID=[], x=[], y=[], z=[], t = [])
I=(position=zeros(3,2),ID=1:2,record=deepcopy(df))
I=Individuals(I)
```
