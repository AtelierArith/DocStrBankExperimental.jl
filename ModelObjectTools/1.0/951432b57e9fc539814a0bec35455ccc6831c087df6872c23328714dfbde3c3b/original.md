compareModelObjects(mo1, mo2; tol=1.0e-15, verbose=false)

Compares two model objects field by field. Output has the format (differences, max*abs*diff), where differences is a vector stipulating the observed differences and max*abs*diff is the maximum absolute value of differences across all fields.
