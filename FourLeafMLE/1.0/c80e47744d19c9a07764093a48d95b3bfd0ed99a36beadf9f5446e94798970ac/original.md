```
test_data_genericity(SITE_PATTERN_DATA)
```

# Description

Test whether a data vector is generic. Here, 'generic' means that for each pair of leaves, i and j, there exists at least one site such that the base pair at leaf i differs from the base pair at leaf j. The functions in this package cannot handle non-generic data without errors.

# Examples

```
test_data_genericity([1,0,0,0,0,0,0,0])

test_data_genericity([1,3,5,0,0,9,5,4])

```
