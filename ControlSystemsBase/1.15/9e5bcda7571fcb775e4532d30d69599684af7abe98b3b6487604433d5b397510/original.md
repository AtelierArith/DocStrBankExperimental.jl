```
relative_gain_array(G, w::AbstractVector)
relative_gain_array(G, w::Number)
```

Calculate the relative gain array of `G` at frequencies `w`.  G(iω) .* pinv(tranpose(G(iω)))

The RGA can be used to find input-output pairings for MIMO control using individually tuned loops. Pair the inputs and outputs such that the RGA(ωc) at the crossover frequency becomes as close to diagonal as possible. Avoid pairings such that RGA(0) contains negative diagonal elements. 

  * The sum of the absolute values of the entries in the RGA is a good measure of the "true condition number" of G, the best condition number that can be achieved by input/output scaling of `G`, -Glad, Ljung.
  * The RGA is invariant to input/output scaling of `G`.
  * If the RGA contains large entries, the system may be sensitive to model errors, -Skogestad, "Multivariable Feedback Control: Analysis and Design":

      * Uncertainty in the input channels (diagonal input uncertainty). Plants with

    large RGA-elements around the crossover frequency are fundamentally   difficult to control because of sensitivity to input uncertainty (e.g. caused   by uncertain or neglected actuator dynamics). In particular, decouplers or   other inverse-based controllers should not be used for plants with large RGAeleme

      * Element uncertainty. Large RGA-elements imply sensitivity to element-by-element uncertainty.

    However, this kind of uncertainty may not occur in practice due to physical couplings   between the transfer function elements. Therefore, diagonal input uncertainty   (which is always present) is usually of more concern for plants with large RGA elements.

The relative gain array is computed using the The unit-consistent (UC) generalized inverse Reference: "On the Relative Gain Array (RGA) with Singular and Rectangular Matrices" Jeffrey Uhlmann https://arxiv.org/pdf/1805.10312.pdf
