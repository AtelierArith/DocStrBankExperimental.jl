```
occurrence(key; [returntype])
occurrence(occurrence::Occurrence; [returntype])
occurrence(datasetKey, occurrenceID; [returntype])
```

`key`、`datasetKey` と `occurrenceID` で、または `Occurrence` オブジェクトを渡すことで、単一の [`Occurrence`](@ref) を取得します。

# キーワード

  * `returntype` は返り値を変更し、`:fragment` または `:verbatim` にすることができます。

# 例

```julia
using GBIF2
sp = species_match("Falco punctatus")
ocs = occurrence_search(sp)
oc = occurrence(ocs[1]; returntype=:verbatim)

# 出力
GBIF2.Occurrence({
                                              "key": 3556750430,
                                       "datasetKey": "4fa7b334-ce0d-4e88-aaae-2e0c138d049e",
                                 "publishingOrgKey": "e2e717bf-551a-4917-bdc9-4fa0f342c530",
                                  "installationKey": "7182d304-b0a2-404b-baba-2086a325c221",
                                "publishingCountry": "MU",
                                         "protocol": "DWC_ARCHIVE",
                                      "lastCrawled": "2022-03-02T17:41:33.833+00:00",
                                       "lastParsed": "2022-09-08T14:55:01.342+00:00",
                                          "crawlId": 15,
                                       "extensions": {},
   "http://rs.gbif.org/terms/1.0/publishingCountry": "MU",
             "http://rs.tdwg.org/dwc/terms/country": "Mauritius",
      "http://rs.tdwg.org/dwc/terms/collectionCode": "EBIRD",
               "http://rs.tdwg.org/dwc/terms/order": "Falconiformes",
                "http://rs.tdwg.org/dwc/terms/year": "2021",
      "http://rs.tdwg.org/dwc/terms/vernacularName": "Mauritius Kestrel",
            "http://rs.tdwg.org/dwc/terms/locality": "Ebony Forest Reserve Chamarel",
       "http://rs.tdwg.org/dwc/terms/basisOfRecord": "HumanObservation",
              "http://rs.tdwg.org/dwc/terms/family": "Falconidae",
               "http://rs.tdwg.org/dwc/terms/month": "07",
     "http://rs.tdwg.org/dwc/terms/decimalLatitude": "-20.436033",
      "http://rs.tdwg.org/dwc/terms/taxonConceptID": "avibase-D1069C26",
      "http://rs.tdwg.org/dwc/terms/scientificName": "Falco punctatus",
          "http://rs.tdwg.org/dwc/terms/recordedBy": "obsr2637790",
       "http://rs.tdwg.org/dwc/terms/stateProvince": "Black River",
              "http://rs.tdwg.org/dwc/terms/phylum": "Chordata",
              "http://rs.gbif.org/terms/1.0/gbifID": "3556750430",
                 "http://rs.tdwg.org/dwc/terms/day": "15",
               "http://rs.tdwg.org/dwc/terms/genus": "Falco",
             "http://rs.tdwg.org/dwc/terms/kingdom": "Animalia",
              "http://purl.org/dc/terms/identifier": "OBS1201437854",
               "http://rs.tdwg.org/dwc/terms/class": "Aves",
     "http://rs.tdwg.org/dwc/terms/individualCount": "1",
     "http://rs.tdwg.org/dwc/terms/specificEpithet": "punctatus",
        "http://rs.tdwg.org/dwc/terms/occurrenceID": "URN:catalog:CLO:EBIRD:OBS1201437854",
       "http://rs.tdwg.org/dwc/terms/catalogNumber": "OBS1201437854",
    "http://rs.tdwg.org/dwc/terms/decimalLongitude": "57.37246",
     "http://rs.tdwg.org/dwc/terms/institutionCode": "CLO",
       "http://rs.tdwg.org/dwc/terms/geodeticDatum": "WGS84",
    "http://rs.tdwg.org/dwc/terms/occurrenceStatus": "PRESENT"
})
```
