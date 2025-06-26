FROM golang:1.21-alpine AS builder
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -ldflags '-extldflags "-static" -w -s' -o hello hello.go

FROM scratch
COPY --from=builder /app/hello /hello
CMD ["/hello"]