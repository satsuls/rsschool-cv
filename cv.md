### 1. Sultan Satubaldinov
### 2. e-mail: ssatubaldinov@gmail.com
### 3. Hard working, easy learning person. I want to develop my programming skills to high level.
### 4. I have liitle experience in python, golang, git.
### 5. 
```
package main

import (
	"fmt"
	"net/http"
	"text/template"
)

var templates *template.Template

func main() {
	fs := http.FileServer(http.Dir("templates"))
	http.Handle("/templates/", http.StripPrefix("/templates/", fs))
	templates = template.Must(template.ParseGlob("templates/*.html"))
	http.HandleFunc("/", askiiHendler)
	http.ListenAndServe(":8080", nil)
}

func askiiHendler(w http.ResponseWriter, r *http.Request) {
	if r.URL.Path != "/" {
		w.WriteHeader(404)
		fmt.Fprintf(w, "404 not found")
		return
	}
	switch {
	case r.Method == "GET":
		templates.ExecuteTemplate(w, "index.html", nil)
	case r.Method == "POST":
		inputtedText := r.FormValue("inputtedText")
		font := r.FormValue("font")
		templates.ExecuteTemplate(w, "index.html", askii(inputtedText, font))
	}
}
``` 
### 6. You can see my projects in my github repos https://github.com/status .
### 7. Now i am styding in programming school alem. 
### 8. I have pre-intermediate level. 