```
    pdDocValidateSignatures(doc::PDDoc; export_certs=false) -> Vector{Dict{Symbol, Any}}
```

## Input

| param        | Description                                                    |
|:------------ |:-------------------------------------------------------------- |
| doc          | The document for which all the signatures are to be validated. |
| export_certs | Optional keyword parameter when set, exports all the           |
|              | certificates that are embeded in the PDF document. These       |
|              | certificates can be for end-entities or one or more certifying |
|              | authorities.                                                   |
|              | Certificates are exported to the file `<PDF filename>.pem`.    |

## Output

Vector of dictionary objects representing one dictionary object for each signature. The dictionary objects map the symbols to output as per the following table. 

| Symbol         | Description                                                   |
|:-------------- |:------------------------------------------------------------- |
| :Name          | The name of the person or authority signing the document.     |
| :P             | Object reference of the page in which the signature is found. |
| :M             | The `CDDate` when the document was signed.                    |
| :certs         | The certificates associated with every signature object.      |
| :subfilter     | The subfilter of PDF signature object.                        |
| :FQT           | Fully qualified title of the signature form.                  |
| :chain         | The certificate chain that validated the signature.           |
| :passed        | Validation status of the signature (true / false)             |
| :error_message | Error message returned during the validation                  |
| :stacktrace    | The stack dump of where the validation failure occurred       |

## Notes

1. Any additional certificates needed for validating a certificate trust chain has to be added manually to the *Trust Store* file at: `<Package Directory>/data/certs/cacerts.pem` in the PEM format. Normally, certificate authorities (root as well as intermediate) are represented in the trust store.
2. Presence of an end-entity certificate in the *Trust Store* ensures that the chain validation for the certificate does not have to be carried out. However, this is not considered a good practice for certificates as the certificate validation is an important attribute to avoid security breaches in the chain. In case of self-signed certificates with not CA capabilities this may be the only option.
3. Validation of digital signatures are limited to the approval signature validation as per section 12.8.1 of PDF Spec. 1.7. Signatures for permissions and usage rights are not validated as per this method. This API only provides a validation report. It does not modify access to any parts of the document based on the validation output. The consumer of the API needs to take appropriate action based on the validation report as desired in their applications.
4. *Revocation* - When time is embedded in the signature as signing-time attribute or a signed timestamp or PDF sigature dictionary has M attribute, then those are picked up for validation. However, revocation information are not used during validation.
5. *PDF 2.0 Support* - The support is only experimental. While some subfilters like `/ETSI.CAdES.detached` are supported. Document Security Store (DSS) and Document Time Stamp (DTS) has not been implemented.

# Example

```
julia> r = pdDocValidateSignatures(doc);

julia> r[1] # Failure case
Dict{Symbol,Any} with 8 entries:
  :Name          => "JAYANT KUMAR ARORA"
  :P             => 1 0 R
  :M             => D:20190425173659+05'30
  :error_message => "Error in Crypto Library:
                        140322274480320:error:02001002:system library:..."
  :subfilter     => /adbe.pkcs7.sha1
  :stacktrace    => ["error(::String) at error.jl:33",
                     "openssl_error(::Int32) at PDCrypt.jl:96",
                     "PDFIO.PD.PDCertStore() at PDCrypt.jl:148",
                     ...]
  :FQT           => "Signature1"
  :passed        => false

julia> r[1] # Passed case
Dict{Symbol,Any} with 8 entries:
  :Name      => "JAYANT KUMAR ARORA"
  :P         => 1 0 R
  :M         => D:20190425173659+05'30
  :certs     => Dict{Symbol,Any}[Certificate Parameters...]
  :subfilter => /adbe.pkcs7.sha1
  :FQT       => "Signature1"
  :chain     => Dict{Symbol,Any}[Certificate Parameters...]
  :passed    => true

```
