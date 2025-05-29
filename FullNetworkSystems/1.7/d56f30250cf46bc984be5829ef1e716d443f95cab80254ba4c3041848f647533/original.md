Constructors for a `Branch`.  The user has the option to define a `Branch` as a line e.g.

```
line1 = Branch("1", "A", "B", 10.0, 10.0, true, (100.0, 102.0), (5.0, 6.0), 1.0, 1.0)
```

where the final two values (`resistance` and `reactance`) can be left unspecified.  Or the user can define a `Branch`` as a transformer:

```
trnasformer1 = Branch(
    "4", "A", "C", 10.0, 10.0, true, (100.0, 102.0), (5.0, 6.0), 1.0, 1.0, 0.5, 30.0
)
```

where two extra parameters are provided as the end representing `tap` and `angle`.
