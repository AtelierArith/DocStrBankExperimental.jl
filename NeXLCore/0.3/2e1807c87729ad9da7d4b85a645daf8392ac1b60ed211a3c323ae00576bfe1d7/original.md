`NormalizeToUnity` normalizes intensities such that the most intense line in each shell is 1.0.

Example:      weight(NormalizeToUnity, n"Fe L3-M5")==1.0     max(cxr=>weight(NormalizeBySubShell, cxr), characteristic(n"Fe", ltransitions))==1.0
