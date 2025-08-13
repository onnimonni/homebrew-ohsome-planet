# homebrew-tap

This repository is a Homebrew tap for installing tools from the GIScience.

## ohsome-planet
### Usage

To install `ohsome-planet` using Homebrew, run:

```sh
brew install GIScience/tap/ohsome-planet --build-from-source
```

This will install the `ohsome-planet` command-line tool on your system which you can use to convert `.osm.pbf` files to geoparquet.

### Example with duckdb
Running these commands will download dataset for Monaco and querying the number of bus routes in monaco using duckdb:

```sh
curl -O https://download.geofabrik.de/europe/monace-latest.osm.pbf

ohsome-planet contributions --pbf=monaco-latest.osm.pbf --output=monaco

duckdb -c "
    SELECT COUNT(*)
    FROM 'monaco/contributions/latest/*.parquet'
    WHERE tags['route'] = 'bus'
"
``` 

## About

- For more information about `ohsome-planet`, visit the [main project repository](https://github.com/GIScience/ohsome-planet).
