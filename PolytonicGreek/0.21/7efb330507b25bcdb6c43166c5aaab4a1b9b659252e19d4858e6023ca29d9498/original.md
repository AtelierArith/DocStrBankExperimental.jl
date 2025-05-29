Implementatiοn of GreekOrthography's augment function for literary Greek.

```julia
augment(s, ortho)

```

NB: `augment` removes all accents  from the resulting string.

# Parameters

  * `ortho` An instance of a `LiteraryGreekOrthography`
  * `s` An optional string to augment.  If is not included, the function returns

a default augment string that can be applied to verb forms starting with a consonant (except note that ρ doubles after augment in standard literary Greek orthography).
