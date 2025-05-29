Format a value, using the following keyword arguments to control formatting (Bold keywords are not printf standard):

  * width. Integer. Try to fit the output into this many characters. May not be successful.  Sacrifice space first, then commas.
  * precision. Integer. How many decimal places.
  * leftjustified. Boolean
  * zeropadding. Boolean
  * commas. Boolean. Thousands-group separator.
  * signed. Boolean. Always show +/- sign?
  * positivespace. Boolean. Prepend an extra space for positive numbers? (so they align nicely with negative numbers)
  * **parens**. Boolean. Use parenthesis instead of "-". e.g. `(1.01)` instead of `-1.01`. Useful in finance. Note that you cannot use `signed` and `parens` option at the same time.
  * **stripzeros**. Boolean. Strip trailing '0' to the right of the decimal (and to the left of 'e', if any ).

      * It may strip the decimal point itself if all trailing places are zeros.
      * This is true by default if precision is not given, and vice versa.
  * alternative. Boolean. See `#` alternative form explanation in standard printf documentation
  * conversion. length=1 string. Default is type dependent. It can be one of `aAeEfFoxX`. See standard printf documentation.
  * **mixedfraction**. Boolean. If the number is rational, format it in mixed fraction e.g. `1_1/2` instead of `3/2`
  * **mixedfractionsep**. Default `_`
  * **fractionsep**. Default `/`
  * **fractionwidth**. Integer. Try to pad zeros to the numerator until the fractional part has this width
  * **tryden**. Integer. Try to use this denominator instead of a smaller one. No-op if it'd lose precision.
  * **suffix**. String. This strings will be appended to the output. Useful for units/%
  * **autoscale**. Symbol, default `:none`. It could be `:metric`, `:binary`, or `:finance`.

      * `:metric` implements common SI symbols for large and small numbers e.g. `M`, `k`, `μ`, `n`
      * `:binary` implements common ISQ symbols for large numbers e.g. `Ti`, `Gi`, `Mi`, `Ki`
      * `:finance` implements common finance/news symbols for large numbers e.g. `b` (billion), `m` (millions)
