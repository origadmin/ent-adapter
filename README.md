# Ent-Adapter

[![Go Report Card](https://goreportcard.com/badge/github.com/casbin/gorm-adapter)](https://goreportcard.com/report/github.com/casbin/ent-adapter)
[![Go](https://github.com/casbin/ent-adapter/actions/workflows/ci.yml/badge.svg)](https://github.com/casbin/ent-adapter/actions/workflows/ci.yml)
[![Coverage Status](https://coveralls.io/repos/github/casbin/ent-adapter/badge.svg?branch=master)](https://coveralls.io/github/casbin/ent-adapter?branch=master)

Ent Adapter is the [ent](https://github.com/ent/ent) adapter for [Casbin](https://github.com/casbin/casbin). With this library, Casbin can load policy from PostgresSQL/Mysql or save policy to it.

## Description

This project was forked from [ent-adapter](https://github.com/casbin/ent-adapter) with some modifications and optimizations.

## Installation

```shell
go get github.com/origadmin/ent-adapter
```

## Usage

```go
import (
    _ "github.com/go-sql-driver/mysql"
    _ "github.com/jackc/pgx/v5/stdlib"
    _ "github.com/lib/pq"

    // or sqlite3 with cgo
    //_ "github.com/mattn/go-sqlite3"
    // sqlite3 without cgo
    _ "github.com/sqlite3ent/sqlite3"
	
	// or use belows for import all drivers
    _ "github.com/origadmin/toolkits/contrib/database
)

    a, err := NewAdapter("mysql", "root:@tcp(127.0.0.1:3306)/casbin")
    //a, err := NewAdapter("postgres", "user=postgres password=postgres host=127.0.0.1 port=5432 dbname=casbin")
    if err != nil {
        panic(err) 
    }
    e, err := casbin.NewEnforcer("/path/to/model",a)
```

## Notification

The database used in adapter(like casbin) should be created manually before NewAdapter calling.

## Getting Help

- [Casbin](https://github.com/casbin/casbin)

## License

This project is under Apache 2.0 License. See the [LICENSE](LICENSE) file for the full license text.
