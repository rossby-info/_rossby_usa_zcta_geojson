# _rossby_usa_zcta_geojson

[![](https://img.shields.io/badge/JSON-9.02.2025-deeppink.svg?label=zip.min.json)](https://www.rossby.info)
[![](https://img.shields.io/badge/JSON-9.02.2025-deeppink.svg?label=state.min.json)](https://www.rossby.info)
[![](https://img.shields.io/badge/MIT-License-red.svg)](https://opensource.org/license/mit)

## Description

GEOJSON files to the ZCTA ZIP Code Place level (5 digit ZIP Code Tabluation Areas) divided into two sets:
* By County (identified by 5 digit FIPS Code).
* By State (identified by 2 letter Short State abbreviation).

Both data sets are:
* Optimized (Minified) to Precision `4` geo-coordinates (`lon`, `lat`) to improve the file size for better in-browser caching/loading:
  * Stripped of certain meta-data fields to reduce file size.
  * Small, about the size of high-resolution Photographs/Pictures.
    * Under `71 MB`, `71,000 KB` for State files.
    * Under `4.5 MB`, `4,500 KB` for County files.
* Each GEO Location has been cross-validated against several other resources to help ensure accuracy.
  * Some meta-data fields have been dropped.
  * Postive number signs are dropped.
* Each GEO Location has the following supplemental meta data for use in-broswer (e.g. - GEOJSON [Mapbox](https://www.mapbox.com/) rendering, Google Maps [Markers](https://developers.google.com/maps/documentation/javascript/3d/marker-overview), etc.):
  ```json
  "properties": {
    "geo_point_2d": {
      "lat": 30.5229, 
      "lon": -87.7638
    }, 
    "zip": "36576", 
    "county": "Baldwin", 
    "state": "Alabama", 
    "short_state": "AL"
  }
  ```
  * You can use the Rossby.info [Free REST API's](https://www.rossby.info/free) to programmatically Query Location, Place, and other kinds of data.
  * And to supplement/improve the accuracy of [ChatGPT LLM Text](https://platform.openai.com/docs/actions/introduction) Prompt Responses.

### ZCTA's
* The U.S. Postal Service maintains and publishes all ZIP Codes. 
  * Unfortunately, they don't make a *complete list* available. 
  * They helpfully make *individual* ZIP Codes available through the U.S. Postal Service [ZIP Code Lookup Site](https://tools.usps.com/zip-code-lookup.htm).
* The U.S. Census Bureau conducts its Census every 10 Years.
  * [ZIP Code Tabulation Areas](https://www.census.gov/programs-surveys/geography/guidance/geo-areas/zctas.html) are published annually by the U.S. Census Bureau using a mix of 10 Year Census Data and United States Postal Service ZIP Codes.
    * As such, they are a fairly accurate approximations of the actual, current, ZIP Code boundaries but they aren't 100% precise/exact.
    * They are nevertheless widely considered to be among the best ways to represent actual ZIP Code boundaries.

### Why Chunk ZCTA's?

* Supplying all ZCTA ZIP Codes as a single GEOJSON file would be prohibitive. 
  * The size would be in excess of `1 GB` `1,000,000 KB` exeeding the maximum String/File size limits in the Browser. 
* Chunking, cherry-picking specific Regions, Counties, or Sub-Regions:
  * Allow the relevant areas to be sent over-the-wire piecemeal saving on Bandwidth, I/O, and Mobile/Smart Phone connectivity.
  * Enable better Lazy-Loading experiences and simultaneous Files/Regions loading.
  * Can be loaded without complex File Streaming.
  
## Limitations and Data Validation

The following known locations weren't found among the ZCTA Shapefiles:

| FIPS | ZIP | Place | State | 
| --- | --- | --- | --- |
| `09001`	|	`06875` |	`Redding Center` | `CT` |
| `51830`	|	`23186` |	`Williamsburg` | `VA` |
| `51830`	|	`23187` | `Williamsburg` | `VA` |

> As such, ZTCA data for FIPS `51830` and ZIP `06875` are absent from the generated GEOJSON.

> Also, please note that  many **CT** ZIP Codes are P.O. Box specific and were likely excluded from the **CT** source data for that reason.

## Data Provenance and Use

* Try it out for free at [geojson.io](https://geojson.io)
* Converted into JSON, Minified, and modified/altered from:
    * U.S. Census Bureau 5-Digit ZCTA5 2023 [2020 Tabulation Area Shapefile](https://catalog.data.gov/dataset/tiger-line-shapefile-2023-nation-u-s-2020-census-5-digit-zip-code-tabulation-area-zcta5) (Public Domain, GEOJSON)
* Open Source [MIT License](https://opensource.org/license/mit)

## Publication History

* **8.13.2025** - initial publication.
* **9.02.2025** - some ZIP Codes to County FIPS corrected, infilled, or added.

## Resources and Links

* [GitHub](https://github.com/rossby-info/_rossby_usa_zcta_geojson)
* [Rossby.info](https://www.rossby.info/)
* [Mapbox](https://www.mapbox.com/)
* [Google Maps](https://developers.google.com/maps)
* [geojson.io](https://geojson.io)
* [ChatGPT LLM Text](https://platform.openai.com/docs/actions/introduction)
* U.S. Bureau [ZIP Code Tabulation Areas](https://www.census.gov/programs-surveys/geography/guidance/geo-areas/zctas.html)
* U.S. Postal Service [ZIP Code Lookup Site](https://tools.usps.com/zip-code-lookup.htm)