Represents the fractional number of X-rays emitted following the ionization of the sub-shell `ionized` via the characteristic X-ray `z inner-outer`.  Due to cascades, `inner` does not necessarily equal `ionized`. The `ionized` subshell may transition to a valency in `inner` via a combination of Auger, fluorescence or Koster-Kronig transitions.  The various different forms make assumptions about the relationship between `ionized` and `inner`, and about `outer`.

```
fluorescenceyield(ass::AtomicSubShell)::Float64
```

The fraction of relaxations from the specified shell that relax via any radiative transition. (`inner`==`ionized`)

```
fluorescenceyield(cxr::CharXRay)
```

The fraction of ionizations of `inner(cxr)` that relax via the one path `cxr`. `ionized==inner` && outer(cxr)

```
fluorescenceyield(ash::AtomicSubShell, cxr::CharXRay)::Float64
```

The fractional number of `cxr` X-rays emitted (on average) for each ionization of `ash`.  This makes no  assumptions about `inner`, `outer` and `ionized`
