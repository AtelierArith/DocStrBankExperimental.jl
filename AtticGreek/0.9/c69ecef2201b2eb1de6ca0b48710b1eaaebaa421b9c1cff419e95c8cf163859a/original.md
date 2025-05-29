Implementatiοn of GreekOrthography's `augment` function for literary Greek.

```julia
augment(ortho; s)

```

NB: `augment` removes all accents  from the resulting string.

# Parameters

  * `ortho` An instance of an `AtticOrthography`
  * `s` An optional string to augment.  If is not included, the function returns

a default augment string for syllabic augment (i.e., a string that can be applied to verb forms starting with a consonant).
