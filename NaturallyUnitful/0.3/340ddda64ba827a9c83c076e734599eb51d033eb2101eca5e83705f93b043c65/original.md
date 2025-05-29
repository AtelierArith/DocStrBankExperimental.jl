```
natural(q; base=u"eV")
```

Convert `q` to natural units based on the units specified by `base`. If `base` is  unspecified, `natural` will default to `eV`. Currently, `natural` only supports  `base`s with dimensions of energy. For all other `base` you will need to use `unnatrual` ' to convert.

Examples:

```
julia> natural(1u"kg")
5.609588650020686e35 eV

julia> natural(1u"kg", base=u"GeV")
5.609588650020685e26 GeV

julia> natural(1u"m")
5.067730759202785e6 eV^-1

julia> natural(1u"m", base=u"GeV")
5.067730759202785e15 GeV^-1
```
