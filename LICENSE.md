CREATE TABLE public.user_sign
(
  id bigint NOT NULL,
  email character varying[],
  password bit varying[],
  CONSTRAINT user_sign_pkey PRIMARY KEY (id),
  CONSTRAINT user_sign_email_key UNIQUE (email)
)
WITH (
  OIDS=FALSE
);
ALTER TABLE public.user_sign
  OWNER TO postgres;

-- Index: public.user_sign_email_idx

-- DROP INDEX public.user_sign_email_idx;

CREATE INDEX user_sign_email_idx
  ON public.user_sign
  USING hash
  (email COLLATE pg_catalog."default");
