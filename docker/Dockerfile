FROM golang:1.20-alpine AS builder
WORKDIR /app
COPY . .
RUN go env -w GO111MODULE=on
RUN go env -w GOPROXY=https://goproxy.cn,direct
RUN go build -o app .

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /
ENV PORT=8080
COPY --from=builder /app/app .
EXPOSE $PORT
ENTRYPOINT ["./app"]
