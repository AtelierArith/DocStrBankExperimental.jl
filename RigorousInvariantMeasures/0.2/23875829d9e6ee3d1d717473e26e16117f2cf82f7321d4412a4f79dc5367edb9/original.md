dfly inequality for maps with infinite derivatives. 

The strategy to compute it follows a variant of Lemma 9.1 in the GMNP paper: 

  * we find a "problematic set" I by taking a small interval of size radius(branch domain)/2^3 around each endpoint with infinite derivative;
  * we find l such that T >= l for each point in I
  * we compute the dfly coefficients as in the lemma.
  * we repeat the computation replacing 2^3 with 2^4, 2^5, ... 2^15 and take the best estimate among these.
