NautyResults must satisfy the following interface

  * strhsh: string value representing the isomorphism class
  * orbits: partitions of Cset parts into orbits e.g. if E#2 = E#5, then these two elements are symmetric
  * generators: generating automorphisms of the automorphism group
  * ngroup: number of elements in the automorphism group
  * canonmap: isomorphism from the input into the canonoical isomorph
  * canon: canonical isomorph (codom of `canonmap`)
