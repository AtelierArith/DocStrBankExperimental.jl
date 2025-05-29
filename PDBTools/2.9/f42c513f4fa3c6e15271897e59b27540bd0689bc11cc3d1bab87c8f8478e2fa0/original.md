```
ContactMap{Bool|Real}
```

Data structure to store contact maps between residues in a protein structure. The contact map is a matrix of distances between residues. A contact is defined  when the distance between any two atoms of the residues is less than a given threshold `dmax`.

If the distance between two residues is greater than `dmax`, the value in the matrix is `missing`, indicating that there is no contact between the residues. If the distance is less than `dmax`, the value in the matrix is the distance between the residues.

The `gap` parameter is used to calculate contacts between residues separated by a given number of residues. For example, if `gap=3`, the contact map was  calculated between residues separated by at least 3 residues in the sequence.

# Fields

  * `matrix::Matrix{Union{Missing,T}}`: Matrix of distances between residues.
  * `d::T`: Threshold distance for a contact.
  * `gap::Int`: Gap between residues to calculate contacts.

If the contact map was calculated with `discrete=true`, the matrix contains `Bool` values, where `true` indicates a contact and `false` indicates no contact. On the other hand, if `discrete=false`, the matrix contains distances between residues.
