## Simple Validate Email for Go

## Usage

###1# Format

    func main() {
		err := validatemail.ValidateFormat("*!&^4 %@@gmail.com")
		if err != nil {
			fmt.Println(err)
		}
	}

output: `invalid format`

###2# Domain

    func main() {
		err := validatemail.ValidateHost("email@x-lazycious-domain.com")
		if err != nil {
			fmt.Println(err)
		}
	}

output: `unresolvable host`

###3# User

    func main() {
		err := validatemail.ValidateHost("unknown-user-129083726@gmail.com")
		if smtpErr, ok := err.(validatemail.SmtpError); ok && err != nil {
			fmt.Printf("Code: %s, Msg: %s", smtpErr.Code(), smtpErr)
		}
	}

output: `Code: 550, Msg: 550 5.1.1 The email account that you tried to reach does not exist.`
