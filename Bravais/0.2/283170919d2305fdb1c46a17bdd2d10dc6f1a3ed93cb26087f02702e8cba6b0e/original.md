```
volume(Vs::AbstractBasis)
```

Return the volume $V$ of the unit cell associated with the basis `Vs::AbstractBasis{D}`.

The volume is computed as $V = \sqrt{\mathrm{det}\mathbf{G}}$ with with $\mathbf{G}$ denoting the metric matrix of `Vs` (cf. the International Tables of Crystallography,  Volume A, Section 5.2.2.3).

See also [`metricmatrix`](@ref).
